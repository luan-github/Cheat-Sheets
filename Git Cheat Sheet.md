# Lista de comandos Git

## Cria o repositório do Git na pasta atual
    git init

## Status dos arquivos
    git status

## Atualiza o arquivo na área de stage (index) com a área de trabalho
    git add git.txt

## Grava mudanças no repositório. Atualizando a área de stage com o repositório
    git commit -m "Arquivo inicial de comandos"

## Grava um novo commit substituindo e adicionando dados ao anterior
    git commit --amend

## Exibe o histórico de altrações
    git log
## Aponta o repositório local para o repositório do github
    git remote add origin https://github.com/luan-github/...

## Envia as alterações para o github
    git push origin master


## Baixar repositório do github
    git clone https://github.com/luan-github/Comandos-Git.git

## Rastrear todos os novos arquivos adicionados
    git add .

## Rastreia apenas os arquivos da pasta indicada
    git add <pasta>

## Adiciona e comita alterações
    git commit -a -m "Adicionando e comitando alteração"
    Ou
    git commit -am "Adicionando e comitando"

## Lista os dois ultimos commits
    git log -n 2

## Resumo de logs
    git log --oneline

## Resumo com linhas alteradas e removidas
    git log --stat

## Log combinado
    git log -n 2 --oneline --stat

## Exibe a diferença entre duas áreas. Por padrão entre a área de trabalho e de stage (index)
    git diff

## Exibe a diferença entre a área de stage (index) e o repositório
    git diff --cached

## Exibe a diferença entre os arquivos na area de stage e a ultima versão comitada
    git diff --staged

## Exibe a diferença entre duas branchs
    git diff branch_1 branch_2

## Código do último commit
    git log -n 1 --oneline

## Exibe a diferença entre o que foi alterado dentro e fora da área de stage e o comit especificado
    git diff <código>

## Exibe a diferença entre o que foi alterado dentro e fora da área de stage e o comit do HEAD
    git diff HEAD

## Exibe a diferença entre commits
    git diff <commit anterior>..<ultimo commit>

## Exibe as duas ultimas alterações até o commit indicado, incluindo alterações não comitadas
    git diff <commit>~2

## Remove arquivo que já  foi adicionado a área de stage e comitado
    git rm <arquivo>

## Remove arquivo da área de index (stage)
    git rm <arquivo> --cached

## Remove arquivo da área de index (stage) e trabalho antes de ser comitado
      git rm <arquivo> -f

## Renomear
    git mv nome novo_nome

## Mover
    git mv <arquivo> <novodiretorio>/<arquivo>

## Move a referência HEAD  e sincroniza a área de trabalho e index com o repositório
    git checkout branch_2

## Desfaz mudanças não rastreadas (inclusive recuperando arquivos apagados)
    git checkout -- <file>
    git checkout HEAD <file>

## Move a branch atual para um commit específico
    git reset <commit> [default=mixed]

## Move a branch atual para um commit específico sincronizando o repositório com a área de stage (index) apenas.
    git reset --mixed

## Move a branch atual para um commit específico sincronizando o repositório com as áreas de index e trabalho
    git reset --hard

## Move a branch atual para um commit específico sem alterar demais áreas
    git reset --soft

## Remove mudanças da área de stage sem alterar o arquivo
    git reset -- <arquivo>

## Cria novo commit removendo alterações de um commit indicado
    git revert

## Desfaz mudanças comitadas
    git revert --no-edit <commit>

## Criação de repositório remoto
    git init --bare pasta.git # --> repository in /optrepositorios/pasta.git/

## Adicionando repositório remoto
    git remote add servidor(nome) file://192.168.0.1/optrepositorios/pasta.git/(endereço)

## Listar o repositórios
    git remote

## Listar os repositórios com a url inclusa
    git remote -v

# Alterando e removendo os repositórios remotos

## Renomear servidor remoto
    git remote rename name new_name

## Alterar endereço
    git remote set-url servidor(name) new_address

## Enviando commits para o repositório
    git push servidor master

## Sincronização do repositório local
    git pull servidor master

## Listar branches
    git branch

## Visualizar branch com commit
    git branch -v

## Exibe os commits pai
    git log --parents

## Exibe os commits para os quais o master aponta
    git log --decorate

## Resumo de logs com os commits pai de cada commit
    git log --parents --decorate --oneline

## Cria uma nova branch nomeada design
    git branch design

## Troca de branch
    git checkout design

## Cria e troca de branch
    git checkout -b loja

## Deleta branch loja
    git branch -d loja

## Deleta a branch loja se está já possuir commits
    git branch -D loja

## Verifica branchs ainda não mescladas
    git branch --no-merged

## Merge com a branch especificada
    git merge design -m "Mesclando com a branch design"

## Mescla alterações das branchs linearizando o historico de commits
    git rebase design

## Edita interativamente o histórico de commits
    git rebase -i [reference]

## Lista as branchs remotas
    git branch -r

## Lista branchs remotas e locais
    git branch -a

## Lista branchs remotas com seus commits
    git branch -rv

## Compartilhar branchs remotas
    git push origin design

## Desfazer o git rebase
    git reset --hard ORIG_HEAD

## Cria a branch design a partir da branch remota origin/design
    git checkout -b design origin/design

## Cria a branch design a partir da branch remota origin/design
    git checkout -t origin/design

## Obter commits de um repositório remoto
    git fetch origin

## Obtem e mescla os novos commits de uma branch remota com uma branch local
    git pull

## Obetem e mescla novos commits usando rebase
    git pull --rebase

## Remover definitivamente a branch remota origin/contato e a branch contato
    git push origin :contato

## Cria tag
    git tag v1.0

## Lista as tags
    git tag

## Cria tag para o commit 343434
    git tag banners <343434>  

## Deleta a tag banners
    git tag -d banners

## Cria tag anotada
    git tag -a v1.1 -m "liberando versão urgente"

## Exibe informaçãoes da tag anotada
    git show -s v1.1

## Compartilha a tag v1.1
    git push origin v1.1

## Enviar todas as tags
    git push origin --tags

## Abortar o rebase voltando a situação antes da tentativa de mesclagem
    git rebase --abort

## Pular o commit que gerou o conflito
    git rebase --skip

## Finalizar o git rebase após um conflito
    git add <file> seguido de git rebase --continue

## Enviar dados para área de stash e sincroniza as demais áreas com o commit atual
    git stash --include-untracked

## Listar transferências para o stash
    git stash list

## Retomar dados da área de stach
    git stash apply [nameid]

## Limpar área de stash
    git stash clear

## Acessar logs de referências
    git reflog [path to reference in .git]

## Plumbing commands
    git cat-file [-p, -t]
    git hash-object
    git count-objects
    git show-ref master

## Note:
  fetch -> merge -> push = git pull
