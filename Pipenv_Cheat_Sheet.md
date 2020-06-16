### Instalar

    $ pip3 install pipenv

### Criar ou iniciar um projeto
Inciar um ambiente com python 3


    $ pipenv --three

Inciar um ambiente com python 2

    $ pipenv --two

Iniciar um projeto com python 3.7

    $ pipenv --python 3.7

### Localização
Localizar o projeto

    $ pipenv --where

Localizar o ambiente virtual

    $ pipenv --venv

Localizar o interpretador

    $ pipenv --py

### Outros comandos
Instalar um projeto buscando pelas dependências no arquivo Pifile, se houver.

    $ pipenv install

Instalar um projeto ignorando o arquivo Pipfile e instalando a partir do Pipfile.lock

    $ pipenv install --ignore-pipfile

Instalar um projeto buscando pelas dependências nos arquivos Pifiles, incluindo os pacotes para desenvolvimento.

    $ pipenv install --dev

Instalar um pacote

    $ pipenv install django==2.2.6

Instalar um pacote de desenvolvimento

    $ pipenv install --dev nose2

Instalar pacote a partir de um repositório git

    $ pipenv install -e git+https://github.com/requests/requests.git#egg=requests

Ativa ou cria um ambiente

    $ pipenv shell

Instalar a partir de requirements.txt

    $ pipenv install -r ./requirements.txt

Gerar Pipfile.lock

    $ pipenv lock

Imprime gráfico das dependências instaladas

    $ pipenv graph

Verificar vunerabilidades de segurança

    $ pipenv check

Remover um pacote

    $ pipenv uninstall django==2.2.6

Remover todos os pacotes sem alterar o Pipfile

    $ pipenv uninstall --all

Remover todos os pacotes de desenvolvimento

    $ pipenv uninstall --all-dev

Executar comando no ambiente virtual sem explicitamente ativá-lo

    $ pipenv run which python

Para gerar um requirements.txt

    $ pipenv run pip freeze

Remover ambiente
    pipenv --rm

### Nota
Pipfile:

    lista os pacotes utilizados para desenvolvimento ou execução. Em grande medida substitui o requirements.txt

Pipfile.lock:

    especificação detalhada de dependências do projeto para evitar atualizações de pacotes que dependem uns dos outros quebrando a árvore de dependência do projeto. É similar ao resultado do comando pip freeze.
