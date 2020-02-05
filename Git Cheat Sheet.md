# Lista de comandos Git

git init # Cria o repositório do Git na pasta atual

git status # Status dos arquivos

git add "comandos git.txt" # Para que o arquivo seja rastreado

git commit -m "Arquivo inicial de comandos" # Grava mudanças no repositório

git log # Exibe o histórico de altrações

git remote add origin https://github.com/luan-github/... # Aponta o repositório local para o repositório do github

git push origin master # Envia as alterações para o github

git clone https://github.com/luan-github/Comandos-Git.git # baixar repositório do github

git add . # rastrear todos os novos arquivos adicionados

git add <pasta> # rastreia apenas os arquivos da pasta indicada

git commit -a -m "Adicionando e comitando alteração"

git commit -am "Adicionando e comitando"

git log -n 2 # lista os dois ultimos commits

git log --oneline # resumo de logs

git log --stat # resumo com linhas alteradas e removidas

git log -n 2 --oneline --stat # log combinado

git diff # exibe a diferença entre o que foi alterado e o arquivo comitado

git diff --staged # exibe a diferença entre os arquivos na area de stage e a ultima vesao comitada

git log -n 1 --oneline # código do último commit

git diff <código>

git diff HEAD

git diff <commit anterior>..<ultimo commit>

git diff <commit anterior>

git diff <commit>~2 # exibe as duas ultimas alterações até o commit indicado, incluindo alterações não comitadas

git rm <arquivo> # remove arquivo que já  foi adicionado a área de stage e comitado

git mv nome novo_nome

git mv <arquivo> <diretorio>/<novo_nome_arquivo>

git checkout -- <arquivo> # desfaz mudanças não rastreadas (inclusive recuperando arquivos apagados)

git reset -- <arquivo> # remove mudanças da área de stage sem alterar o arquivo

git reset --hard  # remove todas as mudanças da área de stage alterando o arquivos

git revert --no-edit <commit> # desfaz mudanças comitadas

git reset --hard <commit> # desfaz mudanças comitadas até o commit indicado

// Criação de repositórioremoto
git init --bare pasta.git # --> repository in /opt/repositorios/pasta.git/

// Adicionando repositório remoto
git remote add servidor(nome) file://192.168.0.1/opt/repositorios/pasta.git/(endereço)

git remote # listar o repositórios

git remote -v # listar os repositórios com a url inclusa

//Alterando e removendo os repositórios remotos
git remote rename name new_name # renomear servidor remoto

git remote set-url servidor(name) new_address

//Enviando commits para o repositório
git push servidor master

//Sincronização do repositório local
git pull servidor master

//Listar branches
git branch

git branch -v # branch com commit

git log --parents # exibe os commits pai

git log --decorate # exibe os commits para os quais o master aponta

git log --parents --decorate --oneline # Resumo de logs com os commits pai de cada commit

git branch design # cria uma nova branch nomeada design

git checkout design # troca de branch

git checkout -b loja # cria e troca de branch

git branch -d loja # deleta branch loja

git branch -D loja # deleta a branch loja se está já possuir commits

git branch --no-merged # verifica branchs ainda não mescladas

git merge design -m "Mesclando com a branch design"

git rebase design # Mescla alterações das branchs linearizando o historico de commits

git branch -r # lista as branchs remotas

git branch -a # lista branchs remotas e locais

git branch -rv # lista branchs remotas com seus commits

git push origin design # compartilhar branchs remotas

git reset --hard ORIG_HEAD # desfazer o git rebase

git checkout -b design origin/design # cria a branch design a partir da branch remota origin/design
git checkout -t origin/design # cria a branch design a partir da branch remota origin/design

//Obter commits de um repositório remoto
git fetch origin

git pull # obtem e mescla os novos commits de uma branch remota com uma branch local

git pull --rebase # obetem e mescla novos commits usando rebase

git push origin :contato # remover definitivamente a branch remota origin/contato e a branch contato

git tag v1.0 # cria tag

git tag # lista as tags

git tag banners <343434>  # cria tag para o commit 343434

git tag -d banners # deleta a tag banners

git tag -a v1.1 -m "liberando versão urgente" # cria tag anotada

git show -s v1.1 # exibe informaçãoes da tag anotada

git push origin v1.1 # compartilha a tag v1.1

git push origin --tags

git rebase --abort # abortar o rebase voltando a situação antes da tentativa de mesclagem

git rebase --skip # pular o commit que gerou o conflito

git add <file> seguido de git rebase --continue # finalizar o git rebase após um conflito

