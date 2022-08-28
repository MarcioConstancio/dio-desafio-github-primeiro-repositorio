## Terminal Linux - Apresentação

* No prompt de comando:

_nome-do-usuario@nome-da-maquina:~$_

o  usuário 'nome-do-usuario' localizado no diretório '~' da máquina 'nome-da-maquina' não é um superusuário (indicado pelo '$'), ou seja, é um usuário com restrições. Dependendo das restrições aplciadas a este usuário, ele não pode instalar programas, acessar determinados diretórios, não pode excluir arquivos, etc. O superusuário (root) é indicado pelo simbolo '#'.

* comandos são sempre indicados com letras minúsculas.

## Navegando pelo sistema de aquivos

* _pwd_: indica o diretório atual do usuário;

* _cd_: Comando usado para indicar mudança de diretório. 

  * _cd .._ : volta para o diretório anterior
  * _cd /_ : Entra no diretório raiz.

* _ls_: lista os arquivos e diretórios dentro do diretório atual.

* _clear_: comando para limpar a tela (atalho ctrl+l)

* No terminal, a tecla _tab_ pode servir como autocompletar para os comandos e caso tenha mais de algum comando com sintaxe igual, ele mostras as opçĩes disponíveis. 

* _ls | more_: Lista os arquivos/diretórios dentro de um diretório com o uso da função 'more'. Este comando é útil quando não se tem uma barra de rolagem disponível. 

  ## Filtrando arquivos

* _ls p*_: Lista arquivos e diretórios iniciados com a letra p. Além do nome dos diretórios, também são mostrados os diretórios e arquivos internos.

* ls m?g*: Lista arquivos e diretórios iniciados com a letra m, cuja terceira letra seja g, independentemente de qual seja a segunda letra. 

* _touch_: cria arquivo vazio. Ex: _touch arquivo.txt_, cria um arquivo vazio com o nome arquivo.txt

  ## Localizando arquivos

* ls /sys: Lista todos os arquivos que estejam dentro do diretório sys sem que o usuário esteja dentro do diretório sys. 

  * Obs: é possível combinar essa forma de localização com os filtros acima. Ex: ls /sys/p* --> lista todos os arquivos iniciados com a letra p dentro do diretório sys, mesmo o usuário não estando dentro do diretório sys. 

* find -name nome-do-arquivo: Usado para encontrar um arquivo específico. O parâmetro '-name' indica que o arquivo será buscado pelo nome, dado pelo nome-do-arquivo. Obs: Caso não saiba o nome completo do arquivo, pode-se usar o asterisco ao final do nome. Ex: find -name -arq* --> retorna a localização de todos os arquivos iniciados com arq.  

  ## Criando diretórios

* mkdir nome-do-diretório: Cria um diretório chamado nome-do-diretório. É possível criar um diretório mesmo em outro diretório. Basta que antes do nome do arquivo, seja indicado o caminho. Ex: mkdir /Documentos/Planilhas --> Cria o diretório Planilhas dentro do diretório Documentos, mesmo o usuário não estando dentro do diretório Documentos. 

* mkdir 'Nome do Diretório': Para criar um diretório com espaços é necessário usar aspas simples.

  ## Excluindo arquivos e diretórios

* _rmdir_: remove/apaga diretórios, contanto que esteja vazio.

* _rm_: remove/apaga arquivos. 

* rm -rf nome-do-diretorio: remove recursivamente todos os arquivos e diretórios dentro do diretório nome-do-diretório.

## Obtendo ajuda

* `nome-do-comando --help`: o comando --help mostra a ajuda disponível para o comando 'nome-do-comando', incluindo todos os argumentos referentes ao comando. Ex: ls --help lista a descrição e todos os argumentos do comando ls.

* Nem todo comando tem ajuda. Ex: clear

* man nome-do-comando: mostra as ajudas referentes ao comando nome-do-comando em forma de manual, com páginas. 

* Na dúvida, dê um google. 

  ## Executando tarefas administrativas como root

  * Para verificar quem está alocado como administrador, pode-se usar abrir o comando group dentro da pasta etc (ex: cat /etc/group). Nele, aqueles que estiverem no grupo sudo terá autorização de fazer tarefas como administrador.

  * Para executar tarefas como administrados, é necessário estar listado no comando sudo. 

    ## Logando como usuário root

    Em alguns casos, vale a pena logar como usuário root enquanto faz algum trabalho. Isso evita ter que ficar digitando sua senha para cada comando realizado. 

    * Dica: nunca fique logado como usuário root. Ao acabar sua tarefa, volte como usuário regular. 

    * `su`: comando usado para acessar o sistema como root. 

      * Caso não tenha sido cadastrada uma senha para este usuário, use o comando `sudo passwd root` e cadastre uma senha. 

    * su nome-do-usuario: Sai do usuário root e volta para o usuário nome-do-usuário.

      ## Liberando acesso remoto do usuário root

    A informação sobre senha de acesso remoto encontra-se no arquivo /etc/ssh/sshd_config. Para acessá-lo e mudar a  configuração de acesso, basta abrí-lo com um editor de texto.

    Ex: `sudo nano /etc/ssh/sshd_config`. Importante: o comando sudo é necessário pois é preciso ter privilégio de administrador para editar este arquivo. 

    ## Trabalhando com arquivos de texto

    Para usar arquivos de texto no terminal Ubuntu pode-se usasr alguns editores, dentre eles o `vi` e o `nano`. 

    * vi: 

      * Para abrir um arquivo: vi nome-do-arquivo.txt
      * para entrar no modo de edição: pressione a tecla `i`
      * Para sair do modo de edição/inserção: pressione `ESC`
      * Para acessar o menu: pressione `:`.
      * Para salvar e sair: pressione `wq`, referente a *write* e *quit*. 

    * nano:

      O modo de edição/inserção está ativo desde o início do programa. O menu de opções é mostrado na parte inferior da página. Dica: O comando `^` que aparece no menu é, na verdade, o comando `ctrl`.

      ## Histórico de comandos

      * hystory: Apresenta o histórico de comandos 
