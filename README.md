<h1 align="center"> 🚀 Git </h1>

# DEFINIÇÃO

É um sistema de controle de versões distribuído, usado principalmente no desenvolvimento de software, mas pode ser usado para registrar o histórico de edições de qualquer tipo de arquivo (Exemplo: alguns livros digitais são disponibilizados no GitHub e escrito aos poucos publicamente). O Git foi inicialmente projetado e desenvolvido por Linus Torvalds para o desenvolvimento do kernel Linux, mas foi adotado por muitos outros projetos.

# Comandos

* *Versão*
~~~
git --version
~~~

* *Configuração*
~~~
git config --global user.name "Your Name"
git config --global user.email "youremail@domain.com"
~~~

* *Aplicando cores ao Git*
~~~
git config --global color.ui true
~~~

* *Verificando configurações*
~~~
git config --list
~~~

* *Inicializa um repositório Git local*
~~~
git init
~~~

* *Verificando os status*
~~~
git status
~~~

* *Adicionando os arquivos*
~~~
# Adicionando arquivo pelo nome
$ git add filename

# Adicionando todos os arquivos modificados
$ git add -A

# Adicionando todos os arquivos e diretorios modificados
$ git add .

# Seleciona o que muda para adicionar(essa vontade tem por todas as alterações e você pode 'Y' ou 'N' as mudanças)
$ git add -p
~~~

* *Removendo*
~~~
git rm -r [nome-arquivo.txt]	Remove um arquivo (ou pasta)
~~~

* *Stash*
~~~
# Stash alteracoes locais
$ git stash

# Stash alteracoes locais com uma mensagem
$ git stash save "this is your custom message"

# Re-aplicar as alteracoes que foram salvar em um stash anterior
$ git stash apply

# Re-aplicar as alterações que você salvou em um determinado número do stash
$ git stash apply stash@{stash_number}

# Apagar qualquer stash pelo seu numero
$ git stash drop stash@{0}

# Aplicar o stash e logo em seguida retirá-lo do seu stack
$ git stash pop

# 'Release' um estoque especial da sua lista de stash`s
$ git stash pop stash@{stash_number}

# Listar todos os stash`s
$ git stash list

# Mostrar as últimas mudanças nos stash`s
$ git stash show

# Veja detalhes [diff] de um determinado número de stash
$ git diff stash@{0}
~~~

* *Commit*
~~~
# Commitar arquivos da stage
$ git commit -m 'mensagem do commit'

# Adicionar arquivo e commitar
$ git commit nomedoarquivo -m 'mesagem do commit'

# Adicionar arquivos na stage e comitar
$ git commit -am 'mensagem do commit'

# Alterar um Commit
$ git commit --amend 'mensagem do novo commit' ou nenhuma mensagem para manter a mensagem anterior

# Squashing commits juntos
$ git rebase -i
# Isto lhe dará uma interface em seu editor de núcleo:
# Comandos:
#  p, pick = use commit
#  r, reword = use commit, mas editar a mensagem do commit
#  e, edit = use commit, mas parar para alterar
#  s, squash = use commit, mas se juntar ao commit anterior
#  f, fixup = como o "squash", mas descartar esta mensagem de log no commit
#  x, exec = usar comando (o resto da linha) usando shell
~~~

* *Checkout*
~~~
# Criando um branch local
$ git checkout -b nomedobranch

# Clona uma branch remota e muda para ela
$ git checkout -b [nome da branch] origin/[nome da branch]	

# Alternar entre dois branchs (na verdade, isso iria funcionar no terminal, bem como para alternar entre dois diretórios - $ cd -)
$ git checkout nomedobranch

# Muda para a última branch
$ git checkout -

# Descarta modificações de um arquivo
$ git checkout -- [nome-arquivo.txt]
~~~

* *Branch*
~~~
# Deletando um branch local - este não vai deixar você apagar um ramo que ainda não foi mesclado
$ git branch -d nomedobranch

# Deletando um branch local - Isto irá apagar uma branch, mesmo que não tenha sido dados um merge
$ git branch -D nomedobranch

# Remova qualquer refs remote que você tem localmente que foram removidos de seu controle remoto (você pode substituir <origem> para qualquer ramo remoto)
$ git remote prune origin

# Ver todos os branch's, incluindo os locias e branch's remotos
$ git branch -a

# Vendo todos os branch's que foram incorporadas em seu branch atual, incluindo local e remoto
$ git branch -a --merged

# Ver todos os branch's que ainda nao foram criados merge, incluindo locais e remotos
$ git branch -a --no-merged

# Ver o branch atual
$ git branch

# Ver branch's remotos
$ git branch -r
~~~

* *Clonando/Copiando*
~~~
git clone https://github.com/cleibp/baseLinks.git
~~~

* *Branchs remotas*
~~~
# Este irá buscar todas as filiais remotas para você.
$ git fetch origin

# Com os branch's remotos na mão, agora você precisa para verificar o branch que você está interessado, dando-lhe uma cópia de trabalho local:
$ git checkout -b test origin/test

# Deletando um branch remoto
$ git branch -rd origin/nomedobranch
$ git push origin --delete nomedobranch  or  $ git push origin:nomedobranch
~~~

* *Merge*
~~~
git merge [nome da branch]	Faz um merge de uma branch na branch atual
git merge [source branch] [branch alvo]	Faz um merge de uma branch em outra branch

# Primeiro check o branch trunk/master
$ git checkout trunk/master

# Agora merge o novo branch para trunk/master
$ git merge nomedobranch

# Para cancelar o merge
$ git merge --abort
~~~

* *Enviando/Empurrando*
~~~
git push	Envia as alterações para o repositório remoto (branch atual)
git push origin [nome da branch]	Enviar uma branch para seu repositório remoto
git push -u origin [nome da branch]	Envia as alterações da branch informada para um repositório remoto (and selecionar a branch)
git push origin --delete [nome da branch]	Deletar uma branch remota
~~~

* *Atualizando repositório*
~~~
git pull	Atualiza o repositório local para o último commit
git pull origin [nome da branch]	Recebe alterações do repositório remoto
~~~

* *Adicionar repositório remoto*
~~~
git remote add origin ssh://git@github.com/[usuario]/[nome-repositorio].git	Adicionar um repositório remoto
git remote set-url origin ssh://git@github.com/[usuario]/[nome-repositorio].git	Seta um repositório da origin branch para o SSH
~~~

* *Atualizando repositório local com mudanças de um repositório do Github*
~~~
$ git pull origin master
~~~

* *Acompanhando branch existente*
~~~
$ git branch --set-upstream-to=origin/foo foo
~~~

* *Inspeção*
~~~
# Mostrar uma lista de todos os commits em um repositório. Este comando mostra tudo sobre um commit, como commit ID, autor, data e mensagem do commit.
$ git log

# Ver modificações (detalhadas)
$ git log --summary

# Lista os commits que mostram mensagens de commit e mudanças
$ git log -p

# Lista os commit's com uma expressão em comum
$ git log -S 'algumacoisa'

# Lista os commit's de um autor
$ git log --author 'Nome do Autor'

# Mostrar uma lista de commits em um repositório de uma forma mais resumida. Isso mostra uma versão mais curta do commit ID e a mensagem de commit.
$ git log --oneline

# Mostrar uma lista de commits em um repositório desde o dia anteirior
$ git log --since=yesterday

# Mostra o log pelo autor e em busca de termo específico dentro da mensagem de commit
$ git log --grep "term" --author "name"
~~~

* *Redefinindo*
~~~
# Mistura a HEAD com um sha
# Isso permite que você faça coisas como dividir um commit
$ git reset --mixed [sha]

# Upstream master
$ git reset HEAD origin/master -- nomedoarquivo

# A versão mais recente do commit
$ git reset HEAD -- nomedoarquivo

# A versão mais recente antes do commit
$ git reset HEAD^ -- nomedoarquivo

# Mover a HEAD para um commit específico
$ git reset --hard sha

# Redefinir a área de teste e o diretório de trabalho para coincidir com a mais recente confirmação. Além das mudanças unstaging, a flag --hard diz Git para substituir todas as alterações no diretório de trabalho também.
$ git reset --hard
~~~

* *Remote*
~~~
# Mostrar onde "origin" está apontando para e também branch de rastos
$ git remote show origin

# Mostrar onde está apontando para "origin"
$ git remote -v

# Alterar a URL do branch remoto "origin"
$ git remote set-url origin https://github.com/user/repo.git

# Adicionar uma nova origem
# Geralmente utilizada para 'rebase' de forks
$ git remote add [NOME] https://github.com/user/fork-repo.git
~~~

* *Grep*
~~~
# 'Buscas' por partes de uma string em um diretorio
$ git grep 'algumacoisa'

# 'Buscas' por partes de uma string em um diretorio e as cópias -n fora os números de linha onde git encontrou
$ git grep -n 'alguma coisa'

# 'Buscas' por partes de uma string em um contexto (algumas linhas antes e após o termo algumas grepped)
$ git grep -C<número de linhas> 'algumacoisa'

# 'Buscas' por partes de uma string e também mostra linhas ANTES do termo grepped
$ git grep -B<número de linhas> 'algumacoisa'

# 'Buscas' por partes de uma string e também mostra linhas DEPOIS do termo grepped
$ git grep -A<núumero de linhas> 'algumacoisa'
~~~

* *Comparação*
~~~
# Visualizar alterações antes de mesclar
$ git diff [branch original] [branch alvo]

# Veja todos (não-staged) mudanças feitas a um repo local
$ git diff

# Veja todos (staged) mudanças feitas a um repo local
$ git diff --cached

# Confira o que as mudanças entre os arquivos que você cometidos e a repo ao vivo
$ git diff --stat origin/master
~~~

* *Blame*
~~~
# Mostra o histórico de alterações do arquivo com o nome do autor
$ git blame [nomedoarquivo]

# Mostra o histórico de alterações do arquivo com o nome do autor e SHA
$ git blame [nomedoarquivo] -l
~~~

## Contatos

[![Github Badge](https://img.shields.io/badge/-Github-000?style=flat-square&logo=Github&logoColor=white&link=https://github.com/cleibp)](https://github.com/cleibp)
[![Linkedin Badge](https://img.shields.io/badge/-LinkedIn-blue?style=flat-square&logo=Linkedin&logoColor=white&link=https://www.linkedin.com/in/cleitonpaiva/)](https://www.linkedin.com/in/cleitonpaiva/)
[![Whatsapp Badge](https://img.shields.io/badge/-Whatsapp-4CA143?style=flat-square&labelColor=4CA143&logo=whatsapp&logoColor=white&link=https://api.whatsapp.com/send?phone=5516988368457&text=Ola!)](https://api.whatsapp.com/send?phone=5516988368457&text=Ola!)
[![Gmail Badge](https://img.shields.io/badge/-Gmail-c14438?style=flat-square&logo=Gmail&logoColor=white&link=mailto:cleibp@gmail.com)](mailto:cleibp@gmail.com)

Feito com muito ❤️☕👨🏻‍💻 por Cleiton Paiva

