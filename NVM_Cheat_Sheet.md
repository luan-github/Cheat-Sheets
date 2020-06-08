### Install and Update
    curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.3/install.sh | bash

### Verificar instalação
    command -v nvm

### Instalar ultima versão do node.JS
    nvm install node

### Intalar uma versão específica
    nvm install 6.14.4 # ou 10.10.0, 8.9.1, etc

### Listar versões instaladas
    nvm ls

### Ativar outra versão
    nvm use 8.11.2

### Alterar a versão default
    nvm alias default 8.11.3

### Remover uma versão que não está em uso
    nvm unistall 6.14.4 # ou 10.10.0, 8.9.1, etc

### Desativar uma versão em uso
    nvm deactivate

### Instalar ferramentas de desenvolvimento
    sudo apt install build-essential

### Desinstalar pacotes nodejs e npm
    sudo apt remove nodejs npm

### Listar versões disponíveis
    sudo apt remove nodejs npm

### Verificar versão nodejs
    node -v

### Verificar versão npm
    npm -v

### Verificar versão npx
    npx -v

### Desinstalar nvm
    rm -rf "$NVM_DIR"

    Editar ~/.bashrc removendo as linhas:

    export NVM_DIR="$HOME/.nvm"
    [ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh" # This loads nvm
    [[ -r $NVM_DIR/bash_completion ]] && \. $NVM_DIR/bash_completion
