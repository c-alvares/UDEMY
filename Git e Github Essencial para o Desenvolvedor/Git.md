GIT
! arquivo .gitignore = serve para ocultar no git arquivos declarados nele;
    |_-> ** nome do diretório -> serve para ignorar diretórios e subdiretórios;
! Diretórios vazios não são identificados pelos git;
! *.extensão do arquivo = ignora qualquer arquivo com essa extensão;

ESTÁGIOS
untracked = Não monitorado;
tracked = Monitorado;
modified = Modificado;
staged = Alocado;

COMMIT
É o envio ou submissão de arquivos que estão "tracked" para o estágio "staged", isto é, prontos para envio para o "branch" principal. 
É também chamado de snapshot.


COMANDOS:
- git status = verifica a situação do projeto;
- git init = inicia o gerenciamento do projeto criando um repositório vazio;
-----
- git config user.name "nome" = cria no file config do diretório .git o nome do usuário;     |-> configuração local(indicada para redes públicas);
- git config user.email "email" == cria no file config do diretório .git o email do usuário; |-> configuração local(indicada para redes públicas);
- git config --global user.name "nome"   |-> configuração global (recomendada para redes particulres);
- git config --global user.email "email" |-> configuração global (recomendada para redes particulres);
-----
- git add .arquivo = adiciona arquivo untracked(não monitorado) ao controle de monitoramento do git(tracked);
- git add. = adiciona todos os arquivos para serem monitorados;
-----
- git commit -m "mensagem a ser adicionada" = fotografia com mensagem referente ao projeto;
!! É uma boa prática, que a cada alteração feita no projeto, seja dado um commit. 
   Assim são registradas as alterações e garantido que caso seja necessário retornar em um ponto específico do projeto, não se perca trabalho feito.
-----
- git log = dá acesso a todo histórico de commits realizados e seus hashID's. Se colocar -nº, por exemplo, -2, aparecerá os (n)dois últimos commits;
- /informaçãoDesejada = busca no log a informação caso o espaço do terminal seja insuficiente para visualizar (:). Por exemplo: /html;
- b -> volta;
- q -> sai do log;
!! HEAD -> master indica o mais recente commit.
!! Quando é feito o commit, aparece apenas os sete primeiros caracteres do hashID.
-----
- git config core.pager cat = alteração local para ver todos os logs independentemente do tamanho do terminal. 
!! Para virar global é só colocar a flag --global antes do core.
- git config core.pager less = volta a ser compatível com o tamanho do terminal;
- clear = limpa o terminal;
- git log --oneline = apresenta os logs são apresentados de forma simplificada;
- git log --before = "2020-05-16" = busca os logs anteriores a uma determinada data;
- git log --after = "2020-05-10" --2 = busca o log dois últimos commits depois da data determinada;
- git log --since = "2 days ago" = busca o log desde dois dias atrás, "1 week after" uma semana depois;
- git log --author = "Cyro" = busca o log pelo responsável do commit
- git help log = mnual do log, com seus diversos comandos;
-----
- git checkout hashID = volta para o commit desejado, apagando os conteúdos commitdados após o referido commit;
- git checkout master = retorna para o commit mais atual, restaurando o programa;
-----
- git mv programa1.html programa2.html = mv -> move = renomeia o arquivo. No exemplo, foi de programa1 para programa2. O arquivo já está "tracked" pelo git;
- git rm programa2.html = rm -> remove = remove, deleta um arquivo. Após esta ação é só commitar;
!! MV e RM podem ser usados tanto para arquivos quanto para diretórios.
-----
- git diff --staged = compara um arquvio já "commitado" com um que está "staged" pelo git;
- git diff 3959fal = compara o último commit feito com o referenciado pelo hashID. Pressionar "q" para sair;
- git diff ce2573d..2455385 = compara a diferença de um commit até o outro. A ordem é do +antigo para o +novo;
-----
. Situação de mensagem do commit incorreta e se deseja corrigir":
- git commit -- amend -m "Mensagem correta" = 
. Realizado um commit, mas lembra-se que precisava adicionar um novo arquivo naquele commit:
    1) Adicione o arquivo para ser monitorado:
- git add .arquivo.extensão;
    2) Realize o commit com o seguinte comando:
- git commit --amend -m "mensagem para sobrescrever a do último commit";
!! O mesmo vale se precisarmos modificar um arquivo já commitado e quisermos incluí-lo no commit anterior.
-----
. Após adicionar um arquivo, diretório, é possível retirá-lo de "staged" com o seguinte comando:
- git restore --staged arquivo.extensão;
- git checkout arquivo.extensão = retorna o arquivo específico para o commit anterior;
- git reset HEAD --hard = reseta as alterações para o commiut HEAD. O comando har é usado para sobrescrever. É como checkout mas é geral.
!! Se após o HEAD tiver um ^ , indica que é para retornar para o último commit.
-----
____Sessão Intermediária____

- git branch = mostra as branchs do projeto. O asterisco (e a cor) indicam em qual ramo(branch) o usuário está.
- git branch nome_da_branch = criar novo branch
- git checkout nome_da_branch = muda para a branch mencionada
- git branch -d nome_da_branch = deleta a branch mencionada em duas etapas (O git questiona se tem certeza que deseja deletar a branch CASO não tenha sido realizado o "merge") e indica o comando abaixo:
- git branch -D nome_da_branch = Deleta a branch
!!! Para deletar uma branch é necessário estar em outra branch.

- ls = mostra os arquivos/pastas no "Local Storage" armazenamento local
- Ctrl + L = limpa o terminal

- git merge nome_da_branch = concatena, junta os arquivos, pastas, alterações realizadas em uma branch com a master
!! Para verificar informações após o merge, usar o "git log". 
!! Pode-se deletar a branch após o merge, utilizando o -d.
!! Na hora do merge, podem ocorrer conflitos. Quando duas pessoas commitarem alterações no mesmo arquivo, isso ocorrerá.

- git rebase = refaz, remonta a base, isto é, ele junta, similarmente ao "merge", mas diferentemente, ele realoca a "base".
- git checkout -b nome_da_branch = cria uma branch e muda para ela.