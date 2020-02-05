### Versão instalada
conda --version

### Atualizar
conda update conda
conda update anaconda

### Criar ambiente com python versão 3.6.5
conda create --name nome_do_ambiente biopython python=3.6.5

### Ativar ambiente
conda activate nome_do_ambiente

### Remover ambiente
conda remove -n nome_do_ambiente --all

### Listar pacotes
conda list
conda list | grep telegram
conda list | findstr telegram (windows)

### Pesquisar pacote
conda search python-telegram-bot
conda search beautifulsoup4

### Adicionar canal
conda config --add channels conda-forge

### Instalar no ambiente
conda install beautifulsoup4=4.6.0

### Criar copia de um ambiente
conda create --name snapshot --clone myenv

### Informações do ambiente atual
conda info
cond info -e
conda info --envs

