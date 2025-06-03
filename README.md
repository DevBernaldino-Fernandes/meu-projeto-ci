# Meu projecto ACI
# passo a passo:
# A - Criar ou usar um repositório no GitHub
   1. Acesse o site https://github.com.
   2. Clique em "New repository" (ou “+” > New repository).
   3. Dê um nome ao projeto, exemplo: meu-projeto-ci.
   4. Marque a opção "Add a README file" (opcional, ajuda a iniciar).
   6. Clique em Create repository.

# B - Criar a pasta .github/workflows no seu projeto:
   1. No seu computador, abra o projeto em um editor de código como o Visual Studio Code.
   2. Crie uma pasta chamada .github. (o ponto é importante)
   3. Dentro dela, crie outra pasta chamada workflows.

# C - Criar o arquivo de automação YAML (ex: ci.yml)
   1. Dentro da pasta workflows, crie um novo arquivo chamado ci.yml
   2. Exemplo de um ci.yml:
        name: Pipeline de Teste
        # Quando essa automação será executada
        on:
        push:
            branches:
            - main  # executa ao enviar algo para a branch 'main'
        # O que será feito
        jobs:
        build:
            runs-on: ubuntu-latest  # GitHub usará uma máquina virtual Ubuntu
            steps:
            - name: Baixar código do repositório
                uses: actions/checkout@v2
            - name: Instalar dependências Ruby
                run: sudo apt-get install rubygems ruby-dev -y
            - name: Mostrar versão do Ruby
                run: ruby --version
# D - Enviar tudo para o GitHub (fazer o "push")
   1. Abra o terminal no Visual Studio Code ou Git Bash.
   2. Digite os comandos abaixo, um por um:
        git init                         # Inicia o controle de versão, se ainda não tiver feito
        git add .                        # Adiciona todos os arquivos
        git commit -m "Configuração CI"  # Cria o commit com mensagem
        git branch -M main               # Define a branch principal como 'main'
        git remote add origin https://github.com/DevBernaldino-Fernandes/meu-projeto-ci.git
        git push -u origin main          # Envia para o GitHub

