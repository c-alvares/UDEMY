____GIT____<br>
-----
!! arquivo .gitignore = serve para ocultar no git arquivos declarados nele.<br>
    |_-> ** nome do diretório -> serve para ignorar diretórios e subdiretórios.<br>
!! Diretórios vazios não são identificados pelos git.<br>
!! *.extensão do arquivo = ignora qualquer arquivo com essa extensão.<br>

<br>

____ESTÁGIOS____<br>
untracked = Não monitorado.<br>
tracked = Monitorado.<br>
modified = Modificado.<br>
staged = Alocado.<br>

<br>

____COMMIT____<br>
É o envio ou submissão de arquivos que estão "tracked" para o estágio "staged", isto é, prontos para envio para o "branch" principal. 
É também chamado de snapshot.

<br>

____COMANDOS:____
- git status = verifica a situação do projeto.
- git init = inicia o gerenciamento do projeto criando um repositório vazio.
-----
- git config user.name "nome" = cria no file config do diretório .git o nome do usuário     |-> configuração local(indicada para redes públicas).
- git config user.email "email" == cria no file config do diretório .git o email do usuário |-> configuração local(indicada para redes públicas).
- git config --global user.name "nome"   |-> configuração global (recomendada para redes particulres).
- git config --global user.email "email" |-> configuração global (recomendada para redes particulres).

-----
- git add .arquivo = adiciona arquivo untracked(não monitorado) ao controle de monitoramento do git(tracked).
- git add. = adiciona todos os arquivos para serem monitorados.

-----
- git commit -m "mensagem a ser adicionada" = fotografia com mensagem referente ao projeto.

!! É uma boa prática, que a cada alteração feita no projeto, seja dado um commit. 
   Assim são registradas as alterações e garantido que caso seja necessário retornar em um ponto específico do projeto, não se perca trabalho feito.

-----
- git log = dá acesso a todo histórico de commits realizados e seus hashID's. Se colocar -nº, por exemplo, -2, aparecerá os (n)dois últimos commits.

- /informaçãoDesejada = busca no log a informação caso o espaço do terminal seja insuficiente para visualizar (:). Por exemplo: /html.
- b -> volta.
- q -> sai do log.

!! HEAD -> master indica o mais recente commit.<br>
!! Quando é feito o commit, aparece apenas os sete primeiros caracteres do hashID.

-----
- git config core.pager cat = alteração local para ver todos os logs independentemente do tamanho do terminal.

!! Para virar global é só colocar a flag --global antes do core.

- git config core.pager less = volta a ser compatível com o tamanho do terminal.
- clear = limpa o terminal.
- git log --oneline = apresenta os logs são apresentados de forma simplificada.
- git log --before = "2020-05-16" = busca os logs anteriores a uma determinada data.
- git log --after = "2020-05-10" --2 = busca o log dois últimos commits depois da data determinada.
- git log --since = "2 days ago" = busca o log desde dois dias atrás, "1 week after" uma semana depois.
- git log --author = "Cyro" = busca o log pelo responsável do commit.
- git help log = mnual do log, com seus diversos comandos.

-----
- git checkout hashID = volta para o commit desejado, apagando os conteúdos commitdados após o referido commit.
- git checkout master = retorna para o commit mais atual, restaurando o programa.

-----
- git mv programa1.html programa2.html = mv -> move = renomeia o arquivo. No exemplo, foi de programa1 para programa2. O arquivo já está "tracked" pelo git.
- git rm programa2.html = rm -> remove = remove, deleta um arquivo. Após esta ação é só commitar.

!! MV e RM podem ser usados tanto para arquivos quanto para diretórios.

-----
- git diff --staged = compara um arquvio já "commitado" com um que está "staged" pelo git.
- git diff 3959fal = compara o último commit feito com o referenciado pelo hashID. Pressionar "q" para sair.
- git diff ce2573d..2455385 = compara a diferença de um commit até o outro. A ordem é do +antigo para o +novo.
-----
<br>

____Situação de mensagem do commit incorreta e se deseja corrigir":____<br>
- git commit -- amend -m "Mensagem correta" = Realizado um commit, mas lembra-se que precisava adicionar um novo arquivo naquele commit:

    1) Adicione o arquivo para ser monitorado:
 
- git add arquivo.extensão

    2) Realize o commit com o seguinte comando:

- git commit --amend -m "mensagem para sobrescrever a do último commit"

!! O mesmo vale se precisarmos modificar um arquivo já commitado e quisermos incluí-lo no commit anterior.

-----
<br>

____Após adicionar um arquivo, diretório, é possível retirá-lo de "staged" com o seguinte comando:____
- git restore --staged arquivo.extensão;
- git checkout arquivo.extensão = retorna o arquivo específico para o commit anterior;
- git reset HEAD --hard = reseta as alterações para o commiut HEAD. O comando har é usado para sobrescrever. É como checkout mas é geral.
!! Se após o HEAD tiver um ^ , indica que é para retornar para o último commit.
-----

<br>

____Sessão Intermediária____
-----

- git branch = mostra as branchs do projeto. O asterisco (e a cor) indicam em qual ramo(branch) o usuário está.
- git branch nome_da_branch = criar novo branch
- git checkout nome_da_branch = muda para a branch mencionada
- git branch -d nome_da_branch = deleta a branch mencionada em duas etapas (O git questiona se tem certeza que deseja deletar a branch CASO não tenha sido realizado o "merge") e indica o comando abaixo:
- git branch -D nome_da_branch = Deleta a branch
!!! Para deletar uma branch é necessário estar em outra branch.

- ls = mostra os arquivos/pastas no "Local Storage" armazenamento local
- ls -la = mostra os arquivos/pastas incluindo os ocultos no "Local Storage"
- Ctrl + L = limpa o terminal

- git merge nome_da_branch = concatena, junta os arquivos, pastas, alterações realizadas em uma branch com a master
!! Para verificar informações após o merge, usar o "git log". 
!! Pode-se deletar a branch após o merge, utilizando o -d.
!! Na hora do merge, podem ocorrer conflitos. Quando duas pessoas commitarem alterações no mesmo arquivo, isso ocorrerá.

- git rebase = refaz, remonta a base, isto é, ele junta, similarmente ao "merge", mas diferentemente, ele realoca a "base".
- git checkout -b nome_da_branch = cria uma branch e muda para ela.

- pwd = mostra no terminal o caminho da pasta/diretório que se está.

- git clone /caminho_do_repositório_que_quer_clonar . = clona o repositório desejado dentro do diretório.

- touch nome_do_arquivo.extensão = cria novo arquivo através do terminal.

- git fetch = baixa as atualizações (commits) de um repositório remoto mas não as aplica no repositório local, ou seja, não faz o "merge". Dessa forma, permite fazer um "rebase" de um branch ao invés de fazer um "merge".
!! Verifique os arquivos com ls. Os arquivos do "fetch não irão aparecer".
!! Após o fetch, é só relizar o rebase (case não tenha branch, é só digitar "git fetch")
-git pull = é o fetch + rebase

!! É aberto um editor de texto. Pode ser escrito uma mensagem do que está sendo feito
- Ctrl + O = grava as alterações no editor de texto. Apertar "ENTER" para salvar
- Ctrl + X = sai do editor
OU
- Ctrl + C = para iniciar fechamento
- qa: = para voltar ao terminal

!! Repositório Bare : O git é decentralizado. Cada repositório do git é um nó na rede. Toda via, ao se trabalhar principalmente com médios e grandes projetos, é possível definir um repositório com uma central, onde os desenvolvedores, cada um com seu repositório local, submete os códigos/dados. Um exemplo disso de repositório bare é o GitHub.

- git init --bare = cria um repositório vazio com vários diretórios. Não é um .git oculto, ele é um pouco diferente. Como se fosse o conteúdo do .git só que direatamente na pasta. Esse é o bare repositorie. Ele serve de centralizador.

- git push = envia os commits para central, para o repositório remoto (bare).

!! Caso você clone um repositório e não realize a configuração de usuário e email, você terá erro na hora de commitar. (À menos que já esteja configurado um usuário global na máquina).
!! Para verificar, é só acessar o diretório .git. Dentro dele, utilizar o comando:
- cat config = mostra as configurações do git

!! Tags podem ser criadas para definir versões estáveis do projeto. Tags são "entregáveis" do projeto. Ou seja, cada parte do projeto pode ser entregue de forma separada e testado pelo cliente. É semelhante a branchs, mas ao contrário destas, as tags não podem receber novos commits. É gerado uma versão pronta para uso, ainda que incompleta. É definido o estado do repositório.
- git tag nomde_da_tag = cria a tag, sem dar retorno
- git tag = mostra a tag

!! Para mandar para o repositório central(bare), tem que ser realizado um push:
- git push origin(local a ser enviado) v1.0(nome_da_tag).

!! O origin é o repositório de origem, o remoto.
!! Para verificar a tag v1.0 é só executar o comando:
- git checkout nome_da_tag

!! Nese caso só é possível verificar as situação, sem realizar novos commits e alterações. Após a verificação, é só realizar o checkout para master novamente.

- git switch -c nome_da_nova_branch = Caso queira manter os commits da tag, é necessário criar uma nova branch usando esse comando com -c junto do switch.

!! Após a criação da nova branch e realizadas as alterações (criação de arquivo por exemplo), é só adicionar e commitar. Deve-se realizar o checkout para master e fazer o merge. Após isso pode-se adicionar uma nova tag, e então realizar o push para o repositório remoto, para o "origin".

-----

<br>

____Sessão Avançada____
-----

Após a criação de um repositório no GitHub, siga os seguintes passo:

1) Crie um diretório localmente, com o mesmo nome do repositório.
2) Crie um arquivo README.md com as informações que desejar(Sugerido # Nome do repositório).
3) No terminal:<br>
3.1) git init<br>
3.2) git config user.name "usuario"<br>
3.3) git config user.email "usario@email.com"<br>
3.4) git add README.md<br>
3.5) git commit -m "mensagem_desejada"<br>
3.6) git remote add origin https://github.com/user/repositorio.git<br>
3.7) git push -u origin master<br>

Explicando os comandos acima:

a) No diretório é inicializado o repositório git, ou seja, começa a ser monitorado.<br>
b) É configurado o usuário e email<br>
c) É adicionado o arquivo markdown README<br>
d) É feito o commit<br>
e) É registrado o repositório no GitHub localmente. Isto é, do repositório local, submeter código para o repositório remoto. A origem do repositório bare é o link do repositório no GitHub.<br>
f) Executa-se o upstream push(upando para o repositório remoto), passando o nome do repositório (origin) e o nome da branch (master).

!! Caso na máquina não esteja configurado o usuário globalmente, será solicitado o usuário e senha do github.com toda vez que for realizado um push.

- git config credential.helper store = É adicionada uma nova configuração no arquivo de config, para esse projeto. Ou seja, na próxima vez que for feito um push e ser solicitado o usuário e senha, o git salva esses dados e não será necessário informá-los novamente.

!! NÃO é recomendado realizar autenticação conforme o indicado acima pois a senha é armazenada em configurações do git no formato de texto.

- git config --global --unset credential.helper = serve para remover as credenciais globais(usuário e senha).
- git config --unset credential.helper = serve para remover as credenciais locais.

!! Ao recarregar a página do projeto no GitHub, o arquivo README.md estará upado.

- git remote -v = verifica se há algum repositório remoto registrado. Geralmente, aparecem duas linhas com nome de origin(nome padrão escolhido, é recomendado). É mostrado o endereço, e utilizado tanto para "fetch" quanto para "push".
- git clone https://github.com/usuario/repositorio.git = clona o repositório remoto do GitHub.
- git pull origin(nome_do_repositório) master(nome_da_branch)

-----
!! Caso sejam feitas modificações nos arquivos, diretórios do repositório local e estas NÃO FORAM ADICIONADAS ao monitoramento do Git, é possível ELIMINAR essas modificações sem que seja necessário apagar/modificar um arquivo por vez. É só realizar um checkout:

- git checkout -- . = volta todos os arquivos ao estado original do commit.
- git checkout -- arquivo.formato(ex: text.txt) = volta apenas o arquivo mencionado ao estado original do último commit.

!! Caso sejam feitas modificações nos arquivos, diretórios do repositório local e estas FORAM ADICIONADAS ao monitoramento do Git é só dar o seguinte commando:

- git checkout HEAD -- . = tira todos os arquivos adicionados ao monitoramento do git e retorna para a HEAD do commit, excluindo as modificações feitas.
- git checkout HEAD -- arquivo.formato = tira o arquivo específico do monitoramento e retorna para a HEAD do commit.

-----
- git revert commitId(8 dígitos) = Cria um novo commit desfazendo as alterações do commit especificado. Não é desfeito o commit, ele continua registrado no log. É feito um novo sem as mudanças e registrado como "REVERT".

- git reset HEAD~1(o número indica quantos commits deseja-se resetar) = remove o commit. O commit referido não aparecerá mais no log.

-----
<br>

____Resolução de Conflitos____

1) SE ACALME, RESPIRE, TOME UMA ÁGUA E VAMOS LÁ!

2) Os conflitos podem ocorrer em situações que o repositório local, teve modificações em diretórios, arquivos e não foi atualizado(feito o pull) em relação ao diretório remoto, como exemplo, o GitHub.

3) Caso as modificações sejam iguais, isto é, foi realizado uma alteração na linha 50 do arquivo exemplo.txt em ambos os repositórios (local e remoto), haverá um conflito.

4) O próprio Git abre e indica os conflitos, sendo apenas necessário analisar qual alteração irá manter.

5) É possível aceitar, a atual(local), a incoming(remota), ambas ou comparar as mudanças(nessa opção, são visualizadas as diferenças entre o arquivo local e o remoto, sem a possibilidade de alteração). 

6) O merge pode ser feito direto pelo arquivo, ou pelo "editor merge". Nele, é apresentado o arquivo remoto, o local e um terceiro de como ficará o merge. 

7) Caso as modificações sejam em arquivos diferentes, o push do commit do repositório local será rejeitado. Isso ocorre porque o local estará mais antigo em relação ao remoto. MAS, não haverá conflito quando for feito o pull, justamente por serem alterações em arquivos distintos.

-----
<br>

____Colaborando com Projetos Open Soucer____
-----

____Issues____

Questões, tarefas, problemas a serem resolvidas no projeto. É uma excelente forma de gerenciar o projeto.

!! Typo = erro de digitação.

Quando é criado um Issue, eles são ordenados.

O Assingnment serve para direcionar o issue para um dos integrantes da equipe.

É possível definir um "Label"(Rótulo) para issue com intuito de agrupar esses apontamentos. 

Após a correção, comentário, interação sobre a issue, é possível fechá-la.

!! As instruções acima, são apenas executáveis pelo responsável pelo projeto. Terceiros, podem criar a issue e comentá-la.

Ao commitar, é possível fechar as issues. Isso é feito, na mensagem do commit da seguinte forma:
- Closes #número_da_issue_a_ser_fechada

!! Caso haja problema de autenticação de usuário, é recomendado o seguinte comando:

- git remote set-url origin https://usuário_gitGub@github.com/usuário_Git/repositório.git = configura o registro do repositório remoto. Força o referido usuário durante a autenticação no repositório descrito.

-----
____Forks____

Fork é um recurso do GitHub que permite  que o repositório de um terceiro, seja "adquirido/importado" para sí próprio. Isto é, imagine que há um projeto no perfil da Google que seja de interesse. Através do fork, esse repositório será copiado para o seu perfil do GitHub e passará a integrar como um repositório seu, não tendo relação com o projeto original(os commits, colaborares, são independentes dele).

-----
____Pull Request____

Através do Pull Request é feito uma solicitação para que as alterações feitas no projeto open source, sejam incorporadas no projeto original. É uma excelente forma de colaborar com outros projetos.

Nota: Só é possível fazer Pull Requests em projetos que não são de autoria própria. Em caso de forks, é possível.

Quando solicitamos ou recebemos uma pull request, ela funciona como uma issue. Será numerada conforme a sequência de issues. <br>
Caso haja 4 issues, a pull request será a #5.

No caso do recebimento de uma pull request, é possível se comunicar com o solicitante através da sessão "write" agradecendo, questionando sobre o código, etc.

A visualização do arquivo/código é através da aba commits, no símbolo <>.

- git fetch origin pull/#issue(número da pull request)/head:nome_da_branch_a_ser_criada = baixa o commit do pull request e cria uma branch para poder realizar o merge com o projeto.

