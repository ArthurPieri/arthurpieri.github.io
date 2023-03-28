---
title: "Git"
author: "Arthur Pieri"
tags: 
- 
---
## Os comandos Básicos de GIT

- GIT INIT- GIT CLONE- GIT PULL- GIT ADD- GIT COMMIT- GIT PUSH- GIT MERGE

## O QUE É GIT?

Git é um sistema de controle de versões. Ele guarda as mudanças realizadas em um conjunto de arquivos ao longo do tempo, de modo que você possa retornar a uma versão específica depois.Existem outros version control systems (VCS) que trabalham  armazenando as alterações realizadas nos arquivos como em um log.O Git trabalha de uma maneira diferente, O git trata os dados como uma série de snapshots de um mini sistema de arquivos, Com o git, todas as vezes que você commita ou salva o estado do seu projeto, O git basicamente tira uma foto de como todos os seus arquivos estão naquele momento e cria uma referência para essa foto.Por uma questão de eficiência, caso não hajam mudanças em um arquivo, o git cria um link para o ultimo estado idêntico que já está armazenado. Ou seja o Git trata os dados como um fluxo de snapshots.Um outro ponto importante para o Git é o fato de ele trabalhar de maneira distribuida, ou seja, todas as máquinas que fazem um "Git clone" (Falar dele mais pra frente) possuem todo o histórico do projeto, sendo assim a maior parte do trabalho é realizado de maneira local, evitando problemas de rede, latência e etc. As informações são enviadas para o servidor origem (ou ˜origin˜) quando utilizamos o comando Git Push.Git também possui integridade, uma vez que tudo possui um checksum o que torna impossível alterar algum arquivo ou diretório sem o git perceber essas diferenças.Esses checksum sáo hashs de 40 caracteres que sáo muito utilizados mas sua principal aplicação é nos commits: ex: commit 1f3ef05ec4367b34802b6e0d45487322cf7f7367O git basicamente apenas realiza operações de adição de informações sendo quase impossível perder um dado após ele ter sido "commitado".

IMPORTANTEOs arquivos no GIT possuem 3 estados principais:- modified - Significa que existem mudanças mas ainda não foram armazenadas na sua database local- staged - Significa que você marcou o arquivo em sua versão atual para ser adicionado a próximo snapshot (commit)- commited - Significa que está armazenado seguramente na sua base de dados LOCAL.- COMO CONSEGUIR AJUDA COM O GIT$ git help <verb>$ git <verb> --help$ man git-<verb>- GIT BASICS- - INICIANDO UM REPOSITÓRIO [GIT] - - Criar uma pasta para o projetoO que são branchs? e como trocar de branch?[OFF]Como fazer cherrypicking?[OFF]Diferença entre Rebase e Merge[OFF]O que é stage?Pull/Push Request