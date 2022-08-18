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

comando: 

Imagem de perfil do AWS Community BuildersSandipkumar Patel
Sandipkumar Patel para criadores de comunidade da AWS
postado em1º de março • Atualizado em14 de março

Crie um pipeline CICD usando GitHub, CodeBuild, CodeDeploy Part-2
#
ah
#
devops
#
cicd
#
github
Pré-requisitos:

Clone o código-fonte necessário para esta demonstração do github.
Link : https://github.com/nidhi2802/code_deploy_demo

Crie seu próprio repositório github e envie o código baixado em seu repositório.
Arquitetura

Descrição da imagem

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
Comandos para instalar o agente do CodeDeploy
# Installing CodeDeploy Agent
sudo yum update
sudo yum install ruby
# Download the agent (replace the region)
wget https://aws-codedeploy-eu-west-3.s3.eu-west-3.amazonaws.com/latest/install
chmod +x ./install
sudo ./install auto
sudo service codedeploy-agent status

Etapa 6: criar grupo de implantação
No aplicativo CodeDeploy criado anteriormente na Etapa 4, crie Grupo de implantação e mencione a tag da instância do EC2 criada anteriormente para implantar o aplicativo em instâncias com essa tag específica.
Etapa 7: criar um CodePipeline
Na Etapa 1, selecionaremos o GitHub como repositório de código de curso e escolheremos os artefatos a serem armazenados no bucket do S3 criado anteriormente.
Na etapa Build escolheremos o Build Project criado por nós.
No estágio Implementar, selecione o aplicativo de implementação e o grupo criado nas etapas anteriores.
Etapa 8: atualizar a função do IAM para CodePipeline
Aqui, atualizaremos a função do IAM criada pelo CodePipeline e anexaremos a política de acesso que concede acesso total do S3 ao CodePipeline.
Isso é tudo que o pipeline é criado e podemos fazer alterações no repositório do github e verificar o funcionamento do pipeline.


Discussão (0)
Se inscrever
foto
Adicionar à discussão
Código de Conduta • Denunciar abuso
Leia a seguir
imagem de perfil de mishmanners
Recursos sem código do GitHub: explorando mais o GitHub e incentivando seus amigos não desenvolvedores
Michelle Mannering -15 de julho

imagem de perfil cobra
Publique suas próprias imagens do Docker com o GitHub Actions
Fábio -24 de julho

imagem de perfil de bradenriggs
Instalando plug-ins do Unreal Engine do GitHub ou do código-fonte
Braden Riggs -26 de julho

imagem de perfil sadedpv
Alguém copiou meu código no Github e afirmou que era seu próprio projeto.
Sadeedpv -15 de julho


Criadores de comunidade da AWS
Seguir
Construa!
Você gostaria de se tornar um AWS Community Builder? Saiba mais sobre o programa e inscreva-se para participar da próxima vez que as inscrições forem abertas.

Saber mais
Mais de AWS Community Builders
Recursos do AWS Auto Scaling para otimizar custos e garantir a disponibilidade
# aws # escalonamento automático # balanceador de carga # nuvem
Por que (e como) você deve definir um alerta de orçamento da AWS usando dimensões
# aws # nuvem # iniciantes # custo
Anexando volume a uma instância do Linux (EC2) cmd
# aws # armazenamento # linux # ebs
# Installing CodeDeploy Agent
sudo yum update
sudo yum install ruby
# Download the agent (replace the region)
wget https://aws-codedeploy-eu-west-3.s3.eu-west-3.amazonaws.com/latest/install
chmod +x ./install
sudo ./install auto
sudo service codedeploy-agent status

Etapa 6: criar grupo de implantação
No aplicativo CodeDeploy criado anteriormente na Etapa 4, crie Grupo de implantação e mencione a tag da instância do EC2 criada anteriormente para implantar o aplicativo em instâncias com essa tag específica.

Etapa 7: criar um CodePipeline
Na Etapa 1, selecionaremos o GitHub como repositório de código de curso e escolheremos os artefatos a serem armazenados no bucket do S3 criado anteriormente.
Na etapa Build escolheremos o Build Project criado por nós.
No estágio Implementar, selecione o aplicativo de implementação e o grupo criado nas etapas anteriores.
Etapa 8: atualizar a função do IAM para CodePipeline
Aqui, atualizaremos a função do IAM criada pelo CodePipeline e anexaremos a política de acesso que concede acesso total do S3 ao CodePipeline.
