# Disparo de E-mails Personalizados
Este projeto foi desenvolvido para aplicar conhecimentos em automação com **Python**, **scraping de dados web**, **segurança** e **envio de e-mails profissionais**.  

## Objetivo
Automatizar o envio de convites personalizados por e-mail para os participantes de um bolão online, com uma abordagem segura, escalável e profissional.

## Descrição
O sistema realiza as seguintes etapas de forma automatizada:

**1. Login autenticado**  
O sistema acessa o painel administrativo do site do bolão usando Python e a biblioteca requests, realizando login autenticado.

**2. Extração de dados**  
Com a ajuda do BeautifulSoup, o sistema extrai os nomes e e-mails dos participantes diretamente da tabela de usuários no painel.

**3. Envio de e-mails**  
Os dados extraídos são processados e utilizados diretamente para o envio de e-mails personalizados, sem a necessidade de exportar para CSV.

**4. Formato e design dos e-mails**  
Os e-mails são enviados com conteúdo HTML, garantindo um visual moderno e responsivo. A conexão com o servidor SMTP (Gmail) é feita através da biblioteca smtplib.

**5. Segurança**  
As informações sensíveis, como a senha do e-mail remetente, são armazenadas de forma segura em variáveis de ambiente usando o arquivo .env e a biblioteca python-dotenv.

**6. Conclusão**  
Cada participante recebe um e-mail individualizado com seu nome e um convite exclusivo para participar do bolão.

## Bibliotecas Utilizadas
* **Requests**  
Realiza o **login e a navegação autenticada** no painel do site.

* **BeautifulSoup4**  
**Extrai dados** HTML da tabela de usuários no painel.

* **smtplib**  
Envia os e-mails via protocolo **SMTP** (Gmail).

* **email.mime**  
Estrutura o conteúdo **HTML** dos e-mails.

* **os**  
Acessa **variáveis de ambiente**.

* **python-dotenv**  
Lê as **credenciais** de forma segura a partir do arquivo .env.

## Abordagem de Segurança
A segurança do sistema é uma prioridade, e todas as credenciais sensíveis são tratadas com cuidado:

1. O **login** no painel do site é realizado de forma segura, com manipulação de cookies e tokens anti-CSRF.
2. **Credenciais sensíveis**, como o login e a senha do e-mail remetente, são armazenadas no arquivo .env. Essas credenciais nunca são hardcoded no código-fonte, garantindo maior segurança.

## Integração com o Painel Administrativo

1. O sistema realiza login automaticamente no painel de administração e segue o seguinte fluxo:
2. Navegação nas páginas de usuários: O sistema percorre as páginas do painel (/User/Index?page=1, /User/Index?page=2, etc.) para coletar os dados de todos os usuários.
3. Extração dinâmica dos dados: O sistema captura os dados (nome e e-mail) diretamente do HTML das páginas.
4. Envio imediato de e-mails: Os dados extraídos são usados imediatamente para enviar os e-mails personalizados aos usuários, sem necessidade de salvar os dados em um arquivo CSV.

## Registro de Log
Os resultados do envio são registrados em **log_envio.txt**, localizado na mesma pasta do projeto.

**Para cada tentativa, o log informa:**
1. Nome e e-mail do destinatário
2. Status: **ENVIADO** ou **ERRO**
3. Detalhes do erro (caso ocorra)
