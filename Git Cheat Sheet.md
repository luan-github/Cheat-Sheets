# Lista de comandos Git

## Cria o repositório do Git na pasta atual
```
git init 
```

## Status dos arquivos
```
git status 
```

## Para que o arquivo seja rastreado
```
git add "comandos git.txt" 
```

## Grava mudanças no repositório
```
git commit -m "Arquivo inicial de comandos" 
```

## Exibe o histórico de altrações
```
git log 
```

## Aponta o repositório local para o repositório do github
```
git remote add origin https://github.com/luan-github/... 
```

## Envia as alterações para o github
```
git push origin master 
```

## baixar repositório do github
```
git clone https://github.com/luan-github/Comandos-Git.git 
```

## rastrear todos os novos arquivos adicionados
```
git add . 
```

## rastreia apenas os arquivos da pasta indicada
```
git add <pasta> 
```

## Adiciona e comita alterações
```
git commit -a -m "Adicionando e comitando alteração"

Ou

git commit -am "Adicionando e comitando"
```

## lista os dois ultimos commits
```
git log -n 2 
```

## resumo de logs
```
git log --oneline 
```

## resumo com linhas alteradas e removidas
```
git log --stat 
```

## log combinado
```
git log -n 2 --oneline --stat 
```

## exibe a diferença entre o que foi alterado e o arquivo comitado
```
git diff 
```

# exibe a diferença entre os arquivos na area de stage e a ultima vesao comitada
```
git diff --staged 
```

## código do último commit
```
git log -n 1 --oneline 
```

## exibe a diferença entre o que foi alterado dentro e fora da área de stage e o comit especificado
```
git diff <código>
```

## exibe a diferença entre o que foi alterado dentro e fora da área de stage e o comit do HEAD
```
git diff HEAD
```

## exibe a diferença entre commits
```
git diff <commit anterior>..<ultimo commit>
```

## exibe as duas ultimas alterações até o commit indicado, incluindo alterações não comitadas
```
git diff <commit>~2 
```

## remove arquivo que já  foi adicionado a área de stage e comitado
```
git rm <arquivo> 
```

## Renomear
```
git mv nome novo_nome
```

## Mover
```
git mv <arquivo> <novodiretorio>/<arquivo>
```

## desfaz mudanças não rastreadas (inclusive recuperando arquivos apagados)
```
git checkout -- <arquivo> 
```

## remove mudanças da área de stage sem alterar o arquivo
```
git reset -- <arquivo> 
```

## remove todas as mudanças da área de stage alterando o arquivos
```
git reset --hard  
```

## desfaz mudanças comitadas
```
git revert --no-edit <commit> 
```

## desfaz mudanças comitadas até o commit indicado
```
git reset --hard <commit> 
```

## Criação de repositório remoto
```
git init --bare pasta.git # --> repository in /opt/repositorios/pasta.git/
```

## Adicionando repositório remoto
```
git remote add servidor(nome) file://192.168.0.1/opt/repositorios/pasta.git/(endereço)
```

## listar o repositórios
```
git remote 
```

## listar os repositórios com a url inclusa
```
git remote -v 
```

### Alterando e removendo os repositórios remotos

## Renomear servidor remoto
```
git remote rename name new_name 
```

## Alterar endereço
```
git remote set-url servidor(name) new_address
```

## Enviando commits para o repositório
```
git push servidor master
```

## Sincronização do repositório local
```
git pull servidor master
```

## Listar branches
```
git branch
```

## branch com commit
```
git branch -v 
```

## exibe os commits pai
```
git log --parents 
```

## exibe os commits para os quais o master aponta
```
git log --decorate 
```

## Resumo de logs com os commits pai de cada commit
```
git log --parents --decorate --oneline 
```

## cria uma nova branch nomeada design
```
git branch design 
```

## troca de branch
```
git checkout design 
```

## cria e troca de branch
```
git checkout -b loja 
```

## deleta branch loja
```
git branch -d loja 
```

## deleta a branch loja se está já possuir commits
```
git branch -D loja 
```

## verifica branchs ainda não mescladas
```
git branch --no-merged 
```

## Merge com a branch especificada
```
git merge design -m "Mesclando com a branch design"
```

## Mescla alterações das branchs linearizando o historico de commits
```
git rebase design 
```

## lista as branchs remotas
```
git branch -r 
```

## lista branchs remotas e locais
```
git branch -a 
```

## lista branchs remotas com seus commits
```
git branch -rv 
```

## compartilhar branchs remotas
```
git push origin design 
```

## desfazer o git rebase
```
git reset --hard ORIG_HEAD 
```

## cria a branch design a partir da branch remota origin/design
```
git checkout -b design origin/design 
```

## cria a branch design a partir da branch remota origin/design
```
git checkout -t origin/design 
```

## Obter commits de um repositório remoto
```
git fetch origin
```

## obtem e mescla os novos commits de uma branch remota com uma branch local
```
git pull 
```

## obetem e mescla novos commits usando rebase
```
git pull --rebase 
```

## remover definitivamente a branch remota origin/contato e a branch contato
```
git push origin :contato 
```

## cria tag
```
git tag v1.0 
```

## lista as tags
```
git tag 
```

## cria tag para o commit 343434
```
git tag banners <343434>  
```

## deleta a tag banners
```
git tag -d banners 
```

## cria tag anotada
```
git tag -a v1.1 -m "liberando versão urgente" 
```

## exibe informaçãoes da tag anotada
```
git show -s v1.1 
```

## compartilha a tag v1.1
```
git push origin v1.1 
```

## Enviar todas as tags
```
git push origin --tags
```

## abortar o rebase voltando a situação antes da tentativa de mesclagem
```
git rebase --abort 
```

## pular o commit que gerou o conflito
```
git rebase --skip 
```

## finalizar o git rebase após um conflito
```
git add <file> seguido de git rebase --continue 
```
