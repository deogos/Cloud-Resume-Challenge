# AWS Cloud Resume Challenge
Minha tentativa do [Cloud Resume Challenge](https://cloudresumechallenge.dev/)


# Arquitetura

<img src="img\Architecture.drawio.png">

# Serviços utilizados
* Route 53
* CloudFront
* Lambda
* DyanamoDB
* S3
* Github Actions
* Certificate Manager
* Namecheap

# Etapas do projeto

0. Certificação
   
Ainda não conclui está etapa, uma vez que a certificação Cloud Practitioner tem um custo de $100. Porém, estou determinado em obter essa certificação o mais rápido possível.

1. HTML, CSS, JS

Como Web Design não era objetivo desse projeto eu decidi utilizar um template, feito pelo [Raj Shekhar](https://github.com/rajshekhar26/cleanfolio-minimal) e alterei conforme minhas necessidades.

2. Website estático

Utilizando o console, é possível realizar facilmente o upload dos arquivos para o bucket S3. É importante ressaltar que o acesso ao bucket deve ser restrito ao público e não deve utilizar a configuração de hospedagem web estática.

3. HTTPS

Utilizando o serviço CloudFront, criei uma nova distribuição. É necessário criar e configurar uma nova OAC (Origin Access Control) para permitir apenas requisições originadas do CloudFront.

4. DNS

A parte mais desafiadora para mim foi a configuração inicial do domínio. Inicialmente, procurei uma solução mais acessível e encontrei o pacote para estudantes do GitHub, que oferecia um domínio gratuito através do namecheap. 

Registrei o domínio deogo.me através desse serviço. Em seguida, utilizei o serviço Route 53 da AWS para criar uma zona hospedada, onde inseri meu domínio e configurei os servidores de nomes no namecheap. Além disso, solicitei um certificado SSL/TLS público através do ACM (Amazon Certificate Manager).

No entanto, errei ao cadastra o endereço errado no namecheap, digitando deogo.me em vez de deogos.me (que é meu usuário do GitHub). Tive que contatar o suporte do namecheap para corrigir o erro, o que demandou tempo e esforço. Após a correção, foi necessário reconfigurar todos os detalhes no Route 53. 

5. Database

Para essa parte, apenas criei uma table no serviço DynamoDB. E utilizei da seguinte forma: 

 Chave Primaria                | Atributos |
| -------------------------- | ---------- |
| id | 1      |
| views                   | 1         |


7. API

Desenvolvi uma função Lambda que se conecta a uma tabela no DynamoDB. Sempre que a URL da função é requisitada, ela retorna o número de visualizações e incrementa esse valor na tabela.


8.  Infrastructure as Code

Deveria ter começado com esse passo, pois para importar os recursos já existentes no Terraform é muito complicado, e não funciona direito. Farei esse projeto novamente, mas começando por essa parte.

13. Source Control / CICD

Utilizando o Github actions podemos facilmante criar automações integradas com aws. Criei um arquivo .yml que define a automação. Toda vez que acontece um push, acontece o upload da pasta portifolio no s3.


