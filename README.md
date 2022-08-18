# Create a CICD Pipeline using GitHub, CodeBuild, CodeDeploy 
---

![Captura de tela de 2022-08-18 18-05-38](https://user-images.githubusercontent.com/102867453/185494970-afb0d310-c14a-45ed-a2ce-08ea519bd810.png)

---
Etapa 1: criar papéis do IAM necessários
Crie uma função para a instância do EC2 com permissões para acesso ao CodeDeploy e S3 para baixar o código.
Crie uma função para o serviço CodeDeploy com permissões para acessar o S3 e as funcionalidades básicas do CodeBuild.
Etapa 2: criar bucket do S3 para armazenar o código-fonte e criar artefatos
Etapa 3: criar projeto de compilação de código
Aqui, criaremos um projeto de compilação que pegará o código-fonte do repositório do GitHub e autenticará o AWS CodeBuild para usar o código de nossa conta do GitHub.
Etapa 4: criar aplicativo de implantação
Criaremos um aplicativo CodeDeploy que implantará os aplicativos na instância do EC2.
Etapa 5: iniciar uma instância do EC2 para hospedar o aplicativo
Inicie uma instância do EC2 que terá a função personalizada anexada a ela criada na Etapa 1 e com a tag apropriada para que possa ser usada posteriormente.
Anexe o grupo de segurança com a porta 22 aberta para ssh e a porta 80 aberta para acessar o aplicativo da web.
SSH para instância do EC2 e instale o agente do CodeDeploy para que o CodeDeploy possa implantar o aplicativo.
