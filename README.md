# Desafio Git/Github 
Primeiro repositório criado para *Desafio de Projeto sobre Git/Github*



#### Instalar e configurar o Github

 [Instalador GitHub](https://git-scm.com/downloads)

- <u>git config:</u> A primeira coisa que você deve fazer quando instalar o Git é definir o seu nome de usuário e endereço de e-mail. Isso é importante porque todos os commits no Git utilizam essas informações, e está imutavelmente anexado nos commits que você realiza:

  *git config --global user.name "John Doe"*
  *git config --global user.email johndoe@example.com*

  **OBS: Relembrando, você só precisará fazer isso uma vez caso passe a opção --global, pois o Git sempre usará essa informação para qualquer coisa que você faça nesse sistema. Caso você queira sobrepor estas com um nome ou endereço de e-mail diferentes para projetos específicos, você pode executar o comando sem a opção --global quando estiver no próprio projeto.**

- <u>git help:</u> Se você precisar de ajuda ao usar Git, existem três maneiras de obter a ajuda para qualquer um dos comandos Git:

  *git help {comando}*
  *git {comando} --help*
  *man git- {comando}*

  

**<u>Criando Projeto</u>**

- <u>git init:</u> Você pode obter um projeto Git utilizando duas formas principais. A primeira faz uso de um projeto ou diretório existente e o importa para o Git. A segunda clona um repositório Git existente a partir de outro servidor.

  ##### Inicializando um Repositório em um Diretório Existente

  Caso você esteja iniciando o monitoramento de um projeto existente com Git, você precisa ir para o diretório do projeto e digitar

  *git init*

- <u>git clone:</u> Você clona um repositório com **git clone [url]**. Por exemplo, caso você queria clonar a biblioteca Git do Ruby chamada Grit, você pode fazê-lo da seguinte forma:

  git clone git://github.com/schacon/grit.git

  Se você entrar no novo diretório grit, você verá todos os arquivos do projeto nele, pronto para serem editados ou utilizados. Caso você queira clonar o repositório em um diretório diferente de grit, é possível especificar esse diretório utilizando a opção abaixo:

  *git clone git://github.com/schacon/grit.git mygrit*

  **OBS: Este comando faz exatamente a mesma coisa que o anterior, mas o diretório alvo será chamado *<u>mygrit</u>*.**

**<u>Comandos Básicos</u>**

- <u>git add:</u> Quando um repositório é inicialmente clonado, todos os seus arquivos estarão monitorados e inalterados porque você simplesmente os obteve e ainda não os editou. Conforme você edita esses arquivos, o Git passa a vê-los como modificados, porque você os alterou desde seu último commit. Você seleciona esses arquivos modificados e então faz o commit de todas as alterações selecionadas e o ciclo se repete.

  *git add*

-  <u>git status:</u> A principal ferramenta utilizada para determinar quais arquivos estão em quais estados é o comando:

​	*git status*

​	**<u>OBS:</u>** O comando lhe mostra em qual branch você se encontra. Vamos dizer que você adicione um novo 	arquivo em seu projeto, um simples arquivo **README**. Caso o arquivo não exista e você execute **git status**, você verá o arquivo não monitorado dessa forma:

\# On branch master
\# Untracked files:
\# (use "git add {file}..." to include in what will be committed)
\#
\# README
nothing added to commit but untracked files present (use "git add" to track)

Você pode ver que o seu novo arquivo **README** não está sendo monitorado, pois está listado sob o cabeçalho **"Untracked files"** na saída do comando status. Não monitorado significa basicamente que o Git está vendo um arquivo que não existia na última captura (commit); o Git não vai incluí-lo nas suas capturas de commit até que você o diga explicitamente que assim o faça. Ele faz isso para que você não inclua acidentalmente arquivos binários gerados, ou outros arquivos que você não têm a intenção de incluir. Digamos, que você queira incluir o arquivo **README**, portanto vamos começar a monitorar este arquivo.

- <u>git diff:</u> Se o comando **git status** for muito vago — você quer saber exatamente o que você alterou, não apenas quais arquivos foram alterados — você pode utilizar o comando.

  *git diff*

  **<u>OBS: </u>**Apesar do comando **git status** responder essas duas perguntas de maneira geral, o **git diff** mostra as linhas exatas que foram adicionadas e removidas — o patch, por assim dizer.
  Se você quer ver o que selecionou que irá no seu próximo commit, pode utilizar:

  *git diff --cached*

- git commit: Armazena o conteúdo atual do índice em um novo commit, juntamente com uma mensagem de registro do usuário que descreve as mudanças.
  Se usa o commit depois de já ter feito o **git add**, para fazer o commit:

  *git commit -m "Mensagem"*

​		**<u>OBS:</u>** Para commitar também os arquivos versionados mesmo não estando no Stage basta adicionar o parâmetro -a

​		*git commit **-a** -m "Mensagem"*

​		**<u>OBS:</u>** Refazendo commit quando esquecer de adicionar um arquivo no Stage:

​		*git commit -m "Mensagem" **--amend***

​			**O amend é destrutivo e só deve ser utilizado antes do commit ter sido enviado ao servidor remoto.**

- <u>git reset:</u> Em qualquer fase, você pode querer desfazer alguma coisa. Aqui, veremos algumas ferramentas básicas para desfazer modificações que você fez. Cuidado, porque você não pode desfazer algumas dessas mudanças. Essa é uma das poucas áreas no Git onde você pode perder algum trabalho se fizer errado.
  Para voltar ao último commit:

  *git reset --hard HEAD~1*

  Para voltar ao último commit e mantém os últimos arquivos no Stage:

  *git reset --soft HEAD~1*

  Volta para o commit com a hash XXXXXXXXXXX:

  *git reset --hard XXXXXXXXXXX*

  ##### Recuperando commit apagado pelo git reset

  Para visualizar os hashs

  *git reflog*

  E para aplicar:

  *git merge {hash}*

-  <u>git rm:</u> Para remover um arquivo do Git, você tem que removê-lo dos arquivos que estão sendo monitorados (mais precisamente, removê-lo da sua área de seleção) e então fazer o commit. O comando **git rm** faz isso e também remove o arquivo do seu diretório para você não ver ele como arquivo não monitorado (untracked file) na próxima vez.

  *git rm -f {arquivo}*

  Se você modificou o arquivo e já o adicionou na área de seleção, você deve forçar a remoção com a opção **-f**. Essa é uma funcionalidade de segurança para prevenir remoções acidentais de dados que ainda não foram gravados em um snapshot e não podem ser recuperados do Git.

- <u>git mv:</u> Diferente de muitos sistemas VCS, o Git não monitora explicitamente arquivos movidos.
  É um pouco confuso que o Git tenha um comando **mv**. Se você quiser renomear um arquivo no Git, você pode fazer isso com

  *git mv arquivo_origem arquivo_destino*

  e funciona. De fato, se você fizer algo desse tipo e consultar o status, você verá que o Git considera que o arquivo foi renomeado.

  No entanto, isso é equivalente a rodar algo como:

  *mv README.txt README*
  *git rm README.txt*
  *git add README*

  O Git descobre que o arquivo foi renomeado implicitamente, então ele não se importa se você renomeou por este caminho ou com o comando **mv**. A única diferença real é que o comando **mv** é mais conveniente, executa três passos de uma vez. O mais importante, você pode usar qualquer ferramenta para renomear um arquivo, e usar add/rm depois, antes de consolidar com o commit.







## Links Úteis
[Sintaxe Básica Markdown](https://www.markdownguide.org/basic-syntax/)

[Comandos Git](https://comandosgit.github.io/)

