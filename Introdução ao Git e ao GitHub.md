#             **Introdução ao Git e GitHub**

Durante o Bootcamp Santander Code Girls foram ministradas aulas sobre o funcionamento do Git e do GutHub e proposto um desafio: Criar seu repositório no GitHub e subir arquivos para o mesmo levando em conta as aulas de "Introdução ao Git e ao GitHub" ministradas pelo professor Otávio Reis.

## **O que é Git?**

Git é um sistema de controle de versão desenvolvido por Linus Torvalds (o criador do Linux), o Git oferece *branches* (**ramificações de recursos)**, então cada pessoa da equipe pode separar uma ramificação de recursos em um repositório local isolado para promover mudanças nos códigos. Com esse sistema, podemos acompanhar as mudanças feitas no código base, pois o sistema registra quem efetuou a mudança e permite a restauração do código removido ou modificado. Não há códigos sobrescritos, uma vez que o Git salva múltiplas cópias no repositório. 

## **O que é GitHub?**

É uma ferramenta, o GitHub é um serviço baseado em nuvem que hospeda o sistema de controle de versão (VCS) chamado Git. Permite que os desenvolvedores colaborem e façam mudanças em projetos compartilhados enquanto mantêm um registro detalhado do seu progresso.

###                                        **Instalando o GIT**

[Neste link](https://git-scm.com/downloads) encontramos os arquivos para download das versões do `Git` para Windows, Linux e MacOS.

#### **Comandos**

Os comandos variam de acordo com o Sistema operacional usado, segue uma lista dos principais comandos:

| Windows   | Linux/Apple |                                                           |
| --------- | ----------- | --------------------------------------------------------- |
| cd        | cd          | Navegar entre pastas                                      |
| dir       | ls          | Lista os arquivos (diretórios) na pasta na qual você está |
| mkdir     | mkdir       | criar pasta                                               |
| del/redir | rm/rf       | deletar pastas\repositórios                               |
| cd ..     | cd ..       | Voltar/Retroceder                                         |
| cls       | clear       | Limpa o terminal                                          |

#### **Entendendo como o Git Funciona**

**Sha1 -** Significa Secure Hash Algorithm (algoritmo de hash seguro), é um conjunto de funções hash criptográficas projetadas pela NSA (agência de segurança nacional dos EUA). A encriptação gera um conjunto de caracteres identificador de 40 dígitos - Código único. É uma forma curta de representar um arquivo.

####                                        **Objetos Internos do Git**

**Blobs:** é um tipo de objeto usado para armazenar o tipo, tamanho e o conteúdo (metadados) de cada arquivo em um repositório. 

Estrutura do blob: Tipo do objeto + tamanho do objeto + \0 + conteúdo do arquivo.

**Trees (árvores):** Armazenam os blobs, vai ser responsável por montar toda a estrutura e onde estão localizados os arquivos. 

Estrutura: Tipo do objeto + tamanho do objeto + \0 + blob + sha1 + nome do arquivo.

Diferente da blob, a árvore guarda o nome do arquivo e pode apontar tanto para blobs ou quanto para outras árvores.

**Commits:** Objeto que vai juntar tudo que se está fazendo e dar sentido às alterações. É possível escrever uma mensagem nesse objeto que estará explicando os arquivos da pasta. 

Estrutura: Tipo do objeto + tamanho do objeto + árvore + parente (ou seja, último commit realizado) + autor + mensagem + timestamp (arquivo de tempo).

####                     **Por que o Git é um sistema distribuído seguro?**

Porque todas as cópias de pessoas que estão contribuindo com o desenvolvimento do código são confiáveis, visto que todas as alterações são salvas e criptografadas.

####                                         **Chaves SSH e Tokens**

Tem o objetivo de estabelecer conexão segura e encriptada entre duas máquinas - servidor do GitHub e o nosso ambiente de desenvolvimento.

- *Chave SSH*

Estabelece uma conexão segura e encriptada entre duas máquinas.

Conexão estabelecida com duas chaves, sendo uma pública e outra privada.

- **Gerar Chave no Git Bash:*

1. ssh-keygen -t ed25519 -C [email@gmail.com](mailto:email@gmail.com)

2. selecionar pasta que deseja salvar e a senha

3.  localizar na pasta -> cd /c/Users/...

4. cat id_ed25519.pub

   ##### **Próximo passo é gerar a chave no GitHub:**

   **Como gerar Chave no GitHub:*

Settings > SSH and GPC keys > New SSH key > colar a chave que o git bash retornou após o último passo.

#####         **Voltando ao GitBash**:

**Passo 1**

input: eval $(ssh-agent -s)

output: Agent pid 999

**Passo 2:**

input: ssh-add id_ed25519

output: Enter passphrase for id_ed25519:

input: senha definida anteriormente

output: id_ed25519 ([email@gmail.com](mailto:email@gmail.com))

- Clonar projeto

No github: copiar SSH do projeto

**IMPORTANTE**: cadastrar mesmo e-mail e nome de usuário cadastrados no *GitHub*.

####                                       **Primeiros comandos no Git:**

- **Iniciar GIT**

`git init` (inicializa um repositório)

`git add` (passa o arquivo de untracked para tracked - staged)

`git commit`

<u>*Ummodified*</u> - arquivo que não sofreu modificação 

*<u>Modified</u>* - arquivo que foi modificado / Staged - esperando para ser manipulado

- **Resolvendo conflitos**

`git add.`
`git commit -a`
`git pull origin main`
`git push origin main`

- **Clonar Projeto:**

No gitbash:  `git clone git@github.com:Oliveira/foodfy.git` ou seja, git clone + SSH do projeto

####                                        Criando um repositório

- Criar uma nova pasta no computador;
- Dentro desta pasta, criar um arquivo de texto e nomei-o `README.md`, sendo `md` a extensão para arquivos do tipo `Markdown`
- Neste arquivo nomeado README, escreva a respeito do projeto que está sendo desenvolvido
- Salve o arquivo

##### *Agora, com o primeiro arquivo pronto e salvo, é hora de usarmos o Git:*

- Novamente, dentro da pasta, clique com o botão direito do mouse e selecione *Git Bash Here*
- Agora, na linha de comando do *bash*, digite `git init` para inicializar o repositório

Após o comando acima, é criada uma pasta `.git` dentro da pasta do projeto, e o arquivo `README.md` ainda não foi salvo no repositório do Git;

Para isso, devemos passar o arquivo da pasta (*working directory*) para a área de stage (*staging area*), o que é feito com o comando `git add README.md`;

Agora os arquivos podem ser enviados ao repositório, o que é feito com o comando `git commit`;

Seguindo os seguintes passos:

- `git add README.md` para colocar o arquivo na *staging area*

- `git commit -m "primeiro commit"` para, de fato, enviar o arquivo para o repositório

*Obs: o `-m`  no comando acima é uma tag para mensagem, o que escrevemos entre aspas é uma mensagem que deve indicar as mudanças feitas neste `commit`.*

#### **Se for feita no repositório remoto,  devemos sincronizar usando o comando pull**

- O comando `git pull`, ele irá puxar todas as alterações feitas no repositório do Github para o seu repositório local, após realizar as correções e só realizar o `push` novamente.

