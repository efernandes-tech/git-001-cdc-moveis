# git-001-cdc-moveis

##### Anotações Livro:

2.1 instalando e configurando o git
	- Configurações básicas após instalar e abrir o terminal do git:
		git config --global user.name “EdersonLRF”
		git config --global user.email “edersonluis.rf@gmail.com”
3.1 criando um repositório local
	- Criar repositório:
		git init
	- Criar repositório que já tem o “.git”:
		git init moveis
3.2 rastreando arquivos
	- Estado atual do repositório:
		git status
	- Rastrear um arquivo ou diretório:
		git add arquivo.txt
	- Rastrear todos ainda não rastreados:
		git add .
	- Ignorando arquivos:
		1 – Criar arquivo chamado:
			.gitignore
		2 – Em cada linha do arquivo, escrever o nome dos arquivos para ignorar; ou o tipo de arquivo, exemplo “.class” para projetos em Java;
		3 – Rastrear o arquivo .gitignore (comitar), pois evolui junto com o projeto.
3.3 gravando arquivos no repositório
	- Gravar alterações definitivamente:
		git commit -m “Commit um”
	- Rastrear e gravar, mas somente arquivos já rastreados:
		git commit -am "Commit dois"
3.4 verificando o histórico do seu repositório
	- Verificar o histórico de mudanças do repositório:
		git log
	- Exibir apenas dois últimos do histórico:
		git log -n 2
	- Histórico resumido:
		git log --oneline
	- Exibe o histórico, listando os arquivos alterados e o número de linhas:
		git log --stat
3.5 verificando mudanças nos arquivos rastreados
	- Verificando mudanças não rastreadas (do diretório para stage):
		git diff
	- Em um arquivo especifico:
		git diff arquivo.txt
	- Diferença entre arquivo rastreado e último gravado (da stage para repositório):
		git diff --staged
	- Exibir diferença entre as três áreas (diretório, stage e repositório):
		git diff 123codigodocommit456
	- Diferença entre commits:
		git diff 123codigodocommit1..456codigodocommit2
	- Diferença entre N commits antecedentes (não exibe da stage):
		git diff 123codigodocommit~2
3.6 removendo arquivos do repositório
	- Remover um arquivo:
		git rm produtos.html
3.7 renomeando e movendo arquivos
	- Renomear arquivo:
		git mv original.css novo.css
	- Mover arquivo (diretório deve existir):
		git mv origem.js js/destino.js
3.8 desfazendo mudanças
	- Desfaz alterações ainda não rastreadas (restaura arquivos excluídos q não foram rastreados):
		git checkout -- arquivo.txt
	- Remove da stage e preserva as alterações:
		git reset -- arquivo.txt
	- Remove da stage e retira as alterações, deixando igual no último commit (neste caso para todos os arquivos):
		git reset --hard
	- Desfazer mudanças já comitadas, remove apenas as alterações do commit indicado (usar head ou código do commit):
		git revert --no-edit HEAD
	- Desfaz as mudanças já comitadas e remove o histórico de commits acima (cuidado):
		git reset --hard 123codcommit456
4.1 repositório remoto
	- Criar um repositório remoto (git cria o diretório com arquivos próprios para uso do git):
		git init --bare moveis-ecologicos.git
4.2 adicionando o repositório remoto
	- Adicionando repositório remoto no projeto:
		git remote add servidor C:\Users\Ederson\Desktop\moveis-ecologicos.git
	- Lista os repositórios remotos:
		git remote
	- Lista os repositórios remotos e a url:
		git remote -v
	- Alterar o nome do repositório remoto:
		git remote rename servidor outronome
	- Alterar a url do repositório remoto:
		git remote set-url servidor C:\Users\Andressa\Desktop\moveis-ecologicos.git
4.3 enviando commits para o repositório remoto
	- Enviar commits para o repositório remoto:
		git push servidor master
4.4 clonando o repositório remoto
	- Obter cópia do repositório remoto:
		git clone C:\Users\Eder\Desktop\moveis-ecologicos.git
4.5 sincronizando o repositório local
	- Recebe os commits enviados por terceiros ao servidor:
		git pull servidor master
4.6 protocolos suportados pelo git
	- Local – no próprio computador ou em mesma rede, usa permissões locais.
		file://C:/caminho/repositorio.git
	- SSH – mais utilizado por ser rápido e seguro, serve para leitura e escrita.
		usuario@servidor:/caminho/repositorio.git
	- Git – próprio do git, segue o SSH, mas apenas leitura.
		git://:caminho/repositorio.git
	- HTTP/HTTPS – quando é utilizado controle rígido de segurança.
		http://caminho/repositorio.git
5.5 criando o repositório do projeto
	- Criar o repositório no GitHub, depois, apontar no local:
		git remote add origin https://github.com/edersonlrf/git-001-moveis.git
5.6 enviando os commits do projeto para o github
	- Enviar os commits do local para o repositório:
		git push origin master
5.7 clonando o repositório hospedado no github
	- Clonar um repositório:
		git clone https://github.com/edersonlrf/git-001-moveis.git
5.8 colaborando com projetos open source
	- Vc só consegue enviar commits para projetos que vc possui permissão. Com isto, quando for colaborar com algum projeto, vc precisa fazer um fork do projeto, baixar a sua versão, alterar e subir os commits para sua versão, após, entrar na página da sua versão do projeto e realizar um pull request, o usuário máster do projeto irá receber a lista dos seus commits para decidir se realiza o pull.
6.1 a branch master
	- Listar as branches do repositório (* aponta à atual):
		git branch
	- Listar branches e os commits associados:
		git branch -v
	- Exibir o histórico resumido dos commits, apontando o commit pai de cada um.
		git log --oneline --decorate --parents
6.2 criando uma branch
	- Criar uma branch:
		git branch design
6.2 trocando de branch
	- Ir para a outra branch:
		git checkout design
	- Criar uma nova branch e já trocar para ela:
		git checkout -b loja
6.4 deletando uma branch
	- Deletar uma branch sem commits (vc não pode estar nela):
		git branch -d loja
	- Deletar uma branch com commits que não foram mesclados a outra branch:
		git branch -D loja
6.7 mesclando alterações
	- Verificando branches ainda não mescladas (lista as q tem alterações em relação a atual):
		git branch --no-merged
	- Exibe a branch que recebera as alterações:
		git branch --merged
	- Juntar as alterações de uma branch em outra:
		git merge design -m “Mesclando com outra branch”
	- Mesclar alterações com rebase lineariza o histórico de commits (não recomendado):
		git rebase design
7.1 branches remotas
	- Listar as branches remotas:
		git branch -r
	- Listar as branches locais e remotas:
		git branch -a
	- Listar as branches locais e remotas com o commit:
		git branch -r -v
7.2 compartilhando branches
	- Compartilhar branchs com o servidor:
		git push origin design
7.4 enviando commits para o repositório central
	- Para enviar as alterações para o repositório remoto:
		git push origin master
7.5 obtendo commits de uma branch remota
	- Trazendo commits de um repositório remoto que ainda não estavam presentes localmente:
		git fetch origin
7.6 mesclando branches remotas e locais
	- Mesclando branches remotas e locais com merge:
		git merge origin/master -m “Mesclando orgin/master em master”
	- Mesclando branches remotas e locais com rebase:
		git rebase origin/master
	- Obter e mesclar os novos commits de uma branch local em um remoto:
		git pull
7.7 deletando branch remotas
	- Removendo a branch local:
		git branch -D contato
	- Removendo definitivamente um branch origin/local e remota:
		git push origin :contato
8.1 criando, listando e deletando tags
	- Criando uma tag leve:
		git tag v1.0
	- Listar as tags:
		git tag
	- Criar uma tag para um commit passado:
		git tag banners 246445
	- Deletando tag:
		git tag -d verssao1
8.2 mais informações com tags anotadas
	- Criando uma tag anotada:
		git tag -a v1.1 -m “Liberando versão”
	- Exibir informações de uma tag anotada:
		git show -s v1.1
8.3 compartilhando tags com a sua equipe
	- Compartilhar tag:
		git push origin tag1
	- Compartilhar todas as tags:
		git push origin -tags
9.2 conflitos apos um merge com mudancas em um mesmo arquivo
	- Quando um arquivo possui alterações em um mesmo ponto durante um merge de branches, ele altera o conteudo do arquivo da seguinte forma:
		<<<<<<< HEAD
        	Ficam alterações que fizemos na branch master, que é a branch atual, para qual o HEAD está apontando.
		=======
        	Ficam  alterações que fizemos na branch design.
		>>>>>>> design
9.4 usando uma ferramenta para resolver conflitos
	- Invocar ferramenta para a resolução de conflitos (exibe a lista de ferramentas, Meld é boa):
		git mergetool
	- Definir ferramenta padrão pra resolução de conflitos:
		git config -global merge.tool meld
- Modelos de distribuição de repositórios:
	- Apenas um repositório remoto, central, para onde os repositórios locais apontam;
	- Cada desenvolvedor tem seu fork, um repositório remoto que é uma cópia do projeto, utilizando um repositório central para integração;
	- Uma hierarquia de repositórios para integração.
- Modelos de branches:
	- Utilizar apenas a branch master ;
	- Ter uma branch para cada nova funcionalidade, deixando a master para código pronto para ser entregue;
	- Ter algumas branches por etapa de desenvolvimento, como uma branch de longo prazo para código ainda em construção e uma de curto prazo para correções de bugs urgentes.
