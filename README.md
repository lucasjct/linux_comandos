# linux_comandos 
### Lista de comandos básicos do Linux

### Navegue pelo Índice: :penguin:
<a name="links"></a>
* [Comando Linux para perdir ajuda](#link-a)
* [Comandos Linux para Processos](#link1)
* [Conteúdo de Arquivos](#link-c)
* [Adicionar ou remover diretórios]("link-b")
* [Pesquisar dentro de um arquivo](#link2)
* [Gerenciar situação dos processos](#link3)
* [Gerenciar execução dos programas no terminal](#link4)
* [Permissões e execução de scripts](#link5)
* [Navegando entre diretórios](#link6)
* [Procurar por arquivos ou diretórios](#link7)
* [Alterar senhas e logar com outro usuário](#link8)
* [Variáveis de ambiente e PATH](#link9)
* [Contando caracteres, palarvras de um arquivo e processos em execução](#link10)
* [Instalação de Programa, gerenciador *apt*](#link11)
* [Utilizando o `dpkg` para instalar ou remover programas](#link12)
* [Script de *init* e *service*](#link13)


***  
<a id="link-a"></a>
### Comando Linux para perdir ajuda  

*  `man` < nome_comando>  
ex:  
`mkdir man`   
* Obter respostas de maneira sintética:    
`whatis <comando>`  
ex: 
`whatis pwd`

<a id="link-b"></a>
###  Comando para criar e remover diretório
* Criar:  `mkdir novo_diretorio`  
* Remover: `rm novo_diretorio`  
* Remover sem mensagem de erro:  `rm -f  novo_diretório`  
* Remover diretorio vazio:  `rmdir novo_diretorio` 
 
<a id="link1"></a>
### Comandos Linux para Processos

* `ps -e` Lista todos os procesos em execução. Seria "ps" de process?

* `ps -ef` Lista de maneira detalhada todos os processos

* `ps -ef | grep <nome do processo a ser filtrado>`  Pesquisa o processo específico. O grep direciona a saída do comando e filtra por um termo desejado

* `ps axu`  Também retorna detalhadamente as informações dos processos executados.

* `Kill <id do processo>` - Interrompe a execução do processo

* `kill -9 <id do processo>` - Interrompe o processo abruptamente

<a id="link-c"></a>
### Conteúdo de Arquivos
* Verificar conteúdo de arquivos:  
`cat  <arquivo.txt>`  
* Verificar espaços no arquivo:   
`cat -A <exemplo.py>`   se retornar '^I' é TAB.  
* Listar os registros de baixo para cima:  
 `tac <exemplo.txt>`

* Listar as últimas linhas de um arquivo:  
 `tail <nome_arquivo.html>`  
* Listar as últimas 5 linhas:  
`tail -n5 <arquivo.txt>`  
*Por padrão, o tail exibe as 10 últimas linhas.*   

* Listar as informações do topo do arquivo:    
`head -n1 README.md`  
*Por padrão, são exibidas as 10 primeiras linhas*

* Imprime o conteúdo por ordem alfabética:   
`sort <arquivo.txt>`

 * Imprime o conteúdo por ordem alfabética reversa:   
`sort -r <arquivo.txt>`

* Ordenar iniciando de uma campo específico:  
`sort -k2 <lista.txt>`  
A ordenação será feita a partir da segunda linha.

* Exibir listagem sem duplicidade:  
`uniq <lista.txt>`  
* Exibir só o que está registrado uma única vez:  
`uniq -u <lista.txt>`  
* Exibir registros que se repetem:  
`uniq -d <lista.txt>`
* Contar duplicidade:  
`uniq -c <lista.txt>`  
* Exemplo utilizando os comandos estudados:  
`sort alunos3.txt | uniq -c | sort -r | head -n1`

<a id="link2"></a>
### Pesquisar dentro de um arquivo

* `cat arquivo.txt | grep <"termo a ser buscado">`  
 O termo a ser buscado, no caso precisa ser passado como string, então precisa de aspas. O pipe '|' pegara a saída do comando `cat` e usará como entrada do como `grep`.

<a id="link3"></a>
### Gerenciar situação dos processos

* `top` - Lista os processos em execução, o consumos de recursos como cpu, memória ram para cada um deles. 

* `top -u <id-do-processo>` Exibe as informações de execução de um processo específico.

* Para alterar o tempo de atualização do `top`, com o `top` em execução, basta pressionar a tecla `d` e passar um novo valor.

* `killall <nome do processo>` Mata o conjunto de processos de um mesmo programa
* `killall <nome do processo> -9 ` Mato todo os processos de um software de maneira definitiva


<a id="link4"></a>
### TERMINAL - Gerenciar execução dos programas no terminal

* `pstree` - Exibe a árvores de processos.
* `ctrl + z` e `bg` . O primeiro comando pausa o programa aberto através do terminal (apenas o pausa, o comando `ctrl + c`, seria pra matar a execução). Porém, para o programa continuar em execução em background(bg) e liberar o terminal, após os __*ctrl + c*__ devemos digitar: bg`.

* Para saber quais processos estão sendo executados em background e quais processos estão parados no nosso terminal, utilizamos o comando `jobs`.

* Para trazer o programa para o terminal e deixá-lo travado, `fg`.

* Para executar um programa em background e liberar o terminal desde o ínicio, devemos abrí-lo com o __&__ . Por exemplo: `gedit &`
<a id="link5"></a>
### Permissões e execução de scripts

 * O Linux pode interpretar scripts bash (extensão `.sh`),entre outros programas. Todos arquivos, programas e diretórios, possuem três tipos de permissões: escrita (`w`), leitura (`r`) e execução  (`x`).    
 Para verificar as permissões, basta executar no diretório: `ls -l`. A saída será, ex: `-rw-rw-r-- 1`.

 __obs:__
 ` O primeiro conjunto de três caracteres representa as permissões do dono do arquivo, o segundo, as permissões do grupo e o terceiro, as permissões dos outros usuários.`

 * Para  dar permissões, precisa ser o usuário administrador (que podemos ver ao digitar:  `whoami` ).  As permisões para escrita pode ser concedida, por exemplo: `chmod +w <nome-do-arquivo>`. Para execução seria: `chmod +x <nome-do-arquivo>`. Para retirar a permissão, basta digitar o sinal de subtração, ex: `chmod -w <nome-do-arquivo>`.

 * Para executar um arquivo bash sem permisão de execução, devemos digitar `sh nome-do-arquivo`. Após a permissão de execução (`chmod +x <nome-do-arquivo>`), podemos  executá-lo com: "`./<nome-do-arquivo>`".


<a id="link6"></a>
### Navegando entre diretórios

__obs:__
 `Sempre que quisermos nos referir ao diretório do usuário (/home/nome_do_usuario/), podemos utilizar o ~. `

* Se estivermos no diretório `usr/bin` e quisermos voltar o diretório usuário, basta digitar: `cd ~`

* Se estiver no diretório `usr/bin` e quisermos ir para o `diretorio_usuario/worspace`, basta digitarmos `cd ~/workspace`. 

###  Criar um Arquivo  
*  `touch` + < nome_do_arquivo.extensão >   
Ex: `touch tests.py`

<a id="link7"></a>
### Procurar por arquivos ou diretórios:
* `find <diretório ou arquivo>`
* Caso eu queira encontra algum caminho de algum arquivo ou programa em específico, posso digitar `which <programa>`. Os programas vão retonar o diretório `/usr/bin/meu_programa`. Os programas dentro deste diretório serão executados em qualquer parte do sistema. Sempre precisa ter permissão de superusuário para mover arquivos para lá.
<a id="link8"></a>
### Alterar senhas e logar com outro usuário

+ Para alterar a senha do usuário atual, utilizamos o comando `passwd`. Para alterar a senha do usuário root, utilizamos ``$ sudo passwd`.

* Para logarmos com outro usuário, digitamos `su <nome usuário>`

<a id="link9"></a>
### Variáveis de ambiente e PATH

Variáveis de ambiente são variáveis globais. Ao configurarmos uma variável de ambiente, podemos executá-la de qualquer lugar do sistema operacional. Por exemplo, criando uma programa em bash, no diretório __workspace__, quando seu diretório for configurado na variável de ambiente, poderemos executá-lo de qualquer lugar sem a necessidade de passar seu caminho absoluto. `PATH` e `HOME`, são dois exemplos de variávei de ambinte

* Configurá-la no seguinte arquivo: `gedit .basrc`  
* Escrever a seguinte linha de configuração para declarar a variável de ambiente: `PATH=${PATH}:home/lucasteixeira/workspace`
* `env` - Verificar as variáveis do sistema. Para ser mais específico e encontrar apenas uma: `env | grep "PATH"`.

*"A variável PATH, guarda informações de onde estão nossos arquivos executáveis para que possamos executar um comando sem a necessidade de digitar o caminho absoluto."* Alura.

<a id="link10"></a>
### Contando caracteres, palarvras de um arquivo e processos em execução

* `wc`, sem parâmetros, ele mostra as linhas, numero de palavras e bytes de um arquivo. 
* `wc -l`, Contar o total de linhas de um arquivo ou de uma listagem.  
* `wc -c`, Contar o total de caracters de um arquivo.
* `wc -w`, Contar o total de palavras de uma arquivos

*Posso combinar com `grep` e outras instruções. Ex:*

`ps -e | grep "chrome" | wc -l ` .  
 Aqui estou dizendo, `ps -e` pegue todos os pacotes em execução passa a saída como enrtada para o próximo comaneo, `| grep "chrome"` filtre para os que contenham "chrome", passe como entrada do próximo comando:`| wc -l`, conte a quantidade de execução.


<a id="link11"></a>
### Instalação de Programa, gerenciador *apt*

* `apt` é o gerenciador de pacotes do Ubuntu.

* `sudo apt-get update` - o gerenciador será atualizado com novas versões e features disponíveis.

* `sudo apt-cache search metrics` - o gerenciado buscará na lista de pacotes qual o mais recomendado para o temos buscado após o `.. search`. Uma listagem será disponiblizada no terminal.

* `sudo apt-get install <programa>`, você pode instalar qualquer programa que queira instalar (pode basear na lista retornada com o conando acima).

* `sudo apt-get remove programa`, caso queira remover o programa instalado.
<a id="link12"></a>
### Utilizando o `dpkg` para instalar ou remover programas
* Após baixar o progrma possso instalar (é necessário estar no diretório do arquivo) ou deinstalar com os seguinte comandos:  
`dpkg -i <arquivo.deb>` instalar  
`dpkg -r <nome do pacote>` desinstalar  
 obs: posso desinstalar com o `apt-get remove` se for da preferência.

<a id="link13"></a>
 ### Script de *init* e *service*

 * Com o comando `service` posso __parar__ ou __inicializar__ um processo. Exemplo:
 
* Verificar a execução:   
`ps -e | grep "vsftpd"` .  
Caso esteja listado como executado, posso pausá-lo. Exemplo:    
`sudo service vsftpd stop`  
Se eu quiser inicializá-lo novamente:   
`sudo service vsftpd start`  
Para ver o status destes serviço:  
`sudo service vsftpd status`

__obs:__ um arquivo de inicialização e desligamento localizado em `/etc/init.d/vsftpd` é executável. Sendo assim, podemos executá-lo diretamente com: 
* `/etc/init.d/vsftpd start` - inicalizar  
* `/etc/init.d/vsftpd stop` -parar
 
 Os scripts dentro de `etc/init.d` são executados sempre que o SO é inicializado. Se quiser que um programa seja inicializado e permaneça rodadndo, basta movê-lo para essa pasta.

 *Verificar os serviços neste diretório:   
 `$ ls etc/init.d`
