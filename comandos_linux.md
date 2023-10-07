# Principais comandos úteis do Linux

## Link com alguns comandos principais

[Comandos Linux](https://www.guru99.com/linux-commands-cheat-sheet.html)

---

## Variáveis de ambiente

Mesmo conceito de programação. Um nome que armazena um valor.

Declarando variáveis:

`VARIAVEL1=Linux`

`echo $VARIAVEL1` - Para mostrar o valor da variável, é preciso referênciar com um `$`

Lembrando que essas variáveis declaradas pertencem aquela sessão de terminal em específico. Se eu fechar o terminal, elas somem.

Existem várias variáveis de ambiente que já são setadas automaticamente pelo sistema, por exemplo:

`echo $USER`

`env` - Mostra variáveis de ambiente já setadas (exportadas)

`set` - Mostra todas as variáveis de ambiente da sessão atual

``` comando=`date` ``` - É possível atribuir o resultado de um comando a uma variável. Pra isso se utiliza crase (`) em volta do comando

`echo $$` - Mostra o PID (Process ID) do processo atual.

`export nome_variavel` - Exporta a variável ou algum valor. Dessa forma ela é visível a todos os processos filhos (processo filho não é um novo terminal!) e a outros programas em execução

`export VARIAVEL=3` - Nesse caso eu já crio a variável e exporto


## Comandos básicos e introduções

`su -` - Acessa o usuário root

`exit` - Sair do Shell ou encerrar a execução atual

`comando --help` - Mostra uma ajuda sobre o comando selecionado

`man comando` - Mostra a documentação do comando

`info comando` - Mostra a documentação do comando

`clear` - Limpa a tela do terminal

`source nome_arquivo` - source é um comando interno de shell que é usado para ler e executar o conteúdo de um arquivo (geralmente um conjunto de comandos), passado como um argumento no script de shell atual.

`hostname` - Mostra na tela o nome do host

`gnome-calculator` - Através do bash é possível abrir aplicações que estejam instaladas na máquina apenas chamando o nome dela no terminal

`date ; echo 'Hello World'` - `;` serve para executar comandos sequênciais. Nesse caso executo o comando `date` e logo após o comando `echo`

`echo 'Hello World` - Imprime no terminal mensagens ou variáveis

Quando se utiliza o `\` no bash, significa que o bash não irá interpretar o caracter após a contra barra, exemplo: `cd Área\ de\ Trabalho/`
## Arquivos e diretórios

No Linux, `.` significa o diretório atual e `..` significa o diretório anterior.

`cd` - Navegar entre diretórios

`pwd` - Mostra o diretório atual

`ls` - Lista os arquivos e diretórios

`ls -l` - Lista os arquivos e diretórios de forma mais detalhada

`ls -a` - Lista os arquivos e diretórios ocultos. Arquivos e diretórios ocultos no linux começam com `.`

`cd ..` - Volta 1 nível atrás do diretório atual

`cd ../..` - Volta 2 níveis. É possível fazer isso quantas vezes necessário para voltar ao início

`cd -` - Volta no diretório que estava anteriormente

`cd` - Vai para o home do usuário atual

`cd ~` - Vai para o home do usuário atual

`cd ~/Documentos` - Vai para o home do usuário atual e entra na pasta `Documentos`

`mkdir nome_diretorio` - Cria um diretório

`mkdir -p diretorio1/diretorio2/diretorio3/diretorio4/diretorio5` - Com o parâmetro `-p` é possível criar vários diretórios aninhados ao mesmo tempo

`rmdir nome_diretorio` - Remove um diretório. Esse comando só remove diretórios vazios

`rmdir -p nome_diretorio/nome_diretorio2` - Remove diretórios aninhados

`rm nome_arquivo ou nome_diretorio` - Apaga o arquivo ou diretório

`rm -r nome_diretorio` - Apaga todo o diretório, incluindo os arquivos dentro dele

`touch nome_arquivo.txt` - Cria um arquivo em branco

`open nome_arquivo/nome_pasta` - Abre o arquivo/pasta selecionado

`cp caminho_origem caminho_destino` - Copia o arquivo de origem para o destino

`cp -r caminho_origem caminho_destino` - Copia todo o diretório para o destino

`cp -v caminho_origem caminho_destino` - O parâmetro -v mostra um detalhamento maior ao executar o comando

`mv caminho_origem caminho_destino` - Move um arquivo ou diretório para o destino especificado. Esse comando também renomeia um arquivo ou diretório para o especificado

## Caracteres especiais (curingas)

`ls exemplo*` - Mostra todos os arquivos/pastas que comecem com teste e depois contenha qualquer coisa ou nada

`ls exemplo[12345]` - Mostra tudo que conter dentro dos colchetes

`ls [Ee]xemplo` - Mostra tudo que conter dentro dos colchetes

`ls exemplo[1-5]` - Mostra tudo entre os valores selecionados

`ls {teste, TESTE}` - Mostra tudo que conter entre os valores das chaves

`ls teste?` - Mostra o que foi selecionado mais algum caracter que substitua o `?`. Caso contrário, não mostrará nada

## Link simbólico

Links simbólicos é um arquivo que aponta para outro. Especificamente, é uma referência que aponta para um arquivo ou um diretório.

![Link simbólico](images/image36.png 'LInk simbólico')

Nesse caso, se eu executar o `vboxconfig`, ele está apontando para `usr/lib/virtualbox/postinst-common.` 

`ln -s nome_do_arquivo nome_do_link_simbolico` - Forma de se criar um link simbólico. Nesse caso, escolho um arquivo para ser linkado e crio um nome para o link simbólico. O parâmetro -s é para criar o link simbólico. Em questão de dúvidas, é sempre bom rodar o `comando --help` para consultas

## Arquivar e compactar arquivos e diretórios

Arquivos .tar são um conjunto de arquivos agrupados (isso não é compactar).

`tar cf nome.tar arquivo.png arquivo2.png` - Esse comando irá agrupar os arquivos dentro de `nome.tar`. O comando tar vários argumentos além de `cf`, é bom consultar o --help quando necessário

`tar tf arquivo.tar` - Lista o que tem dentro de arquivo.tar

`tar xf arquivo.tar` - Extrai o arquivo agrupado

`gzip arquivo.tar` - Compacta o arquivo arquivo.tar (seu formato será .gz, enquanto arquivos agrupados são .tar). Nesse caso, como compactei um arquivo .tar, seu formato será `.tar.gz`. Também há o formato `.tgz`, que significa que o arquivo está agrupado e compactado.

`gzip -k arquivo` - Compacta o arquivo mas não exclui o arquivo antigo (parâmetro keep)

`gunzip arquivo` - Descompacta o arquivo

## Procurando por arquivos

`find caminho_a_procurar -name arquivo_a_procurar` - Busca o arquivo selecionado no diretório especificado 

`locate rpm` - Também faz uma busca de arquivos ou diretórios que contenha `rpm` por exemplo. Esse comando é mais rápido pois ele consulta uma base já gerada pelo sistema, porém não se atualiza sozinho, então acaba sendo limitado em relação ao `find`

`whereis tar` - whereis é útil para procurar o caminho do executável de um programa/comando

`which python3` - O which procura nos diretórios da variável de ambiente $PATH

## Manipulando Arquivos de Texto

`cat arquivo_texto.txt` - Lê e mostra na tela o conteúdo do arquivo texto

`less arquivo_texto.txt` - Lê e mostra na tela o conteúdo do arquivo texto

`head arquivo_texto.txt` - Lê e mostra na tela o conteúdo do arquivo texto (as primeiras linhas)

`tail arquivo_texto.txt` - Lê e mostra na tela o conteúdo do arquivo texto (as últimas linhas)

`cat arquivo_texto.txt > novo_arquivo.txt` - Redirecionou a saída do cat para o novo_arquivo.txt. Nesse caso o valor foi atribuído. Se o arquivo já existir, vai sobrescrever, caso queira concatenar no final, utilize `>>` ao invés de `>`

`wc arquivo_texto.txt` - Retorna a quantidade de linhas, palavras e caracteres de um arquivo texto

`sort arquivo_texto.txt` - Ordena um arquivo texto por ordem alfabética. O parâmetro `-r` ordena ao contrário [Z-A]

`uniq arquivo_texto.txt` - Mostra as ocorrências únicas do arquivo (O arquivo precisa estar ordenado)

`cut -c1-10 arquivo_texto.txt` - Pega os caracteres do 1 ao 10 do arquivo texto

`sort arquivo_texto.txt | uniq` - O pipe serve para concatenar comandos. Aqui estou ordenando o `arquivo_texto.txt` e logo após uso a saída desse comando como entrada do comando `uniq`

`grep palavra arquivo_texto.txt` - Filtra a palavra selecionada no arquivo texto

## Editores de texto em linha de comando

Os principais editores de texto via linha de comando do Linux são o `nano` e `vim`

Para editar um arquivo com eles, apenas digite `nano/vim nome_do_arquivo`

O vim trabalha com modos para realizar alterações nos arquivos. São eles: `modo de inserção`, `modo de navegação` e `modo de comando`.

**Modo de navegação:** Modo padrão. É por ele que é possível navegar entre os caracteres do texto

**Modo de inserção:** `i` - Pressione `i` para entrar no modo de inserção (digitar algo no vim). Para sair desse modo e voltar a navegação, pressione `ESC`

**Modo de comando:** Digite `:` para conseguir aplicar qualquer comando ao vim, alguns dos comandos principais são:

`:w` - Salva o arquivo (write).

`:q` - Sai do Vim (quit).

`:wq` - Salva e sai do Vim.

`:q!` - Sai do Vim sem salvar as alterações (forçar saída).

`:w arquivo` - Salva o arquivo com um novo nome.

`:e arquivo` - Abre um novo arquivo no Vim.

`:bnext` ou `:bn` - Navega para o próximo buffer.

`:bprev` ou `:bp` - Navega para o buffer anterior.

`:bd` - Fecha o buffer atual.

`:set nu` - Ativa a exibição do número das linhas.

`:set nonu` - Desativa a exibição do número das linhas.

`/texto` - Pesquisa o texto para frente.

`?texto` - Pesquisa o texto para trás.

`n` - Navega para a próxima ocorrência da pesquisa.

`N` - Navega para a ocorrência anterior da pesquisa.

`dd` - Exclui a linha atual.

`yy` - Copia a linha atual.

`p` - Cola o conteúdo copiado ou excluído.

`u` - Desfaz a última ação.

`Ctrl + r` - Refaz a última ação desfeita.

`:s/antigo/novo/g` - Substitui todas as ocorrências de "antigo" por "novo" na linha atual.

`:%s/antigo/novo/g` - Substitui todas as ocorrências de "antigo" por "novo" no arquivo inteiro

## Gerenciamento de Processos e Serviços

Alguns conceitos importantes sobre processos são `PID` e `PPID`. `PID` (Process ID) é o ID do Processo, já o `PPID` (Parent Process ID) são os filhos do processo pai

`pstree` - Mostra a árvore de processos do Linux

`ps` - Mostra os processos do usuário naquela sessão de terminal

`ps -ux` - Mostra todos os processos do seu usuário

`ps -uxa` - Mostra todos os processos de todos os usuários

`pgrep processo` - Mostra o PID do processo selecionado

`kill pid_do_processo` - Força matar um processo. Há vários argumentos nesse comando, utilize `kill -l` para checar.

`kill -s SIGKILL pid_do_processo` - Utilizando um parâmetro específico do comando kill, nesse caso o `SIGKILL`. Também é possível utilizar o número do parâmetro, no caso do SIGKILL, o número é `9`. `kill -9 pid_do_processo`

`pkill firefox` - Mata o processo pelo nome, sem ter que identificar o PID

`killall apache` - Mata todos os processos daquele programa em específico

**systemctl** é um comando do **systemd** para gerenciar os serviços. Alguns comandos básicos são: 

`systemctl status nome_servico` - Mostra o status do serviço em específico

`systemctl start nome_servico` - Inicia o serviço em específico

`systemctl stop nome_servico` - Para o serviço em específico

`systemctl restart nome_servico` - Reinicia o serviço em específico

Ao executar um processo pelo terminal, esse processo pode rodar em `foreground` ou `background`. Ou seja, ao executar o firefox pelo terminal, ele irá executar o navegador e o processo ficará preso naquele terminal, sem poder executar outros comandos. Isso é rodar em `foreground`. Para rodar em `background`, rode o comando com `&` no final do comando

## Administração do Sistema Linux

`top` - Mostra um relatório geral do uso do sistema Linux

`free -h` - Mostra a quantidade de memória da máquina, o quanto está sendo utilizado e quantidade de memória livre

`uptime` - Informações de quanto tempo a máquina está ligada, quantidade de usuários logados, etc

`uname -a` - Informações do sistema (ex: versão do kernel, arquitetura do sistema, etc)

`df -h` - Mostra as partições da máquina

**Há 2 principais gerenciadores de pacotes no Linux: Os utilizados no padrão Debian (Ubuntu, Linux Mint) e o padrão RedHat (Fedora, CentOS)**

`dpkg` e `apt-get` são os principais utilizados no padrão Debian

**dpkg:**

`dpkg -l` - Lista todos os pacotes instalados na máquina

`dpkg -i nome_pacote.deb` - Após você baixar da internet o pacote, instala via dpkg (O comando dpkg só instala o pacote solicitado, ele não lida com as dependências desse pacote)

`dpkg -s nome_pacote` - Mostra as informações do pacote instalado na máquina

`dpkg -r nome_pacote` - Desinstala o pacote da máquina, mas mantém algumas informações de configuração

`dpkg -P nome_pacote` - Remove completamente o pacote

**apt-get:**

O apt-get é mais completo. Ele baixa o pacote, checa as versões, instala dependências, etc

`apt-get update` - Vai no arquivo **sources.list**, onde contém os links de todos os sites com os pacotes e atualiza a base de informações dos pacotes

`apt-get upgrade` - Consulta os pacotes da máquina e checa se há versões novas, se houver, baixa e as instala

`apt-get install nome_pacote` - Instala a aplicação no PC

`apt-get remove nome_pacote` - Desinstala a aplicação do PC

**Já no padrão RedHat, os principais são:**

`rpm`, `yum` ou `dnf`

**rpm:**

`rpm -qa` - Lista todos os pacotes instalados na máquina

`rpm -i nome_pacote.rpm` - Após você baixar da internet o pacote, instala via rpm (O comando rpm só instala o pacote solicitado, ele não lida com as dependências desse pacote)

`rpm -qi nome_pacote` - Mostra as informações do pacote instalado na máquina

`rpm -e nome_pacote` - Desinstala o pacote da máquina, mas mantém algumas informações de configuração

`rpm -ev nome_pacote` - Remove completamente o pacote

**yum:**

O yum é mais completo. Ele baixa o pacote, checa as versões, instala dependências, etc

`yum check-update` - Atualiza a base de informações dos pacotes

`yum update` - Consulta os pacotes da máquina e checa se há versões novas, se houver, baixa e as instala

`yum install nome_pacote` - Instala a aplicação no PC

`yum remove nome_pacote` - Desinstala a aplicação do PC

**dnf:**

O dnf é o sucessor do yum, porém mantém muitos dos comandos compatíveis

`dnf check-update` - Atualiza a base de informações dos pacotes. Essas informações fica em `fedora.repo`

`dnf upgrade` - Consulta os pacotes da máquina e checa se há versões novas, se houver, baixa e as instala

`dnf install nome_pacote` - Instala a aplicação no PC

`dnf remove nome_pacote` - Desinstala a aplicação do PC

`reboot` - Reinicia o Linux

`shutdown/poweroff` - Desliga o PC

Os principais logs do sistema ficam dentro de `/var/log`

`syslog` - Mostra os logs do sistema

`dmesg` - Mostra os logs do sistema. Também possui informações de log do boot do sistema

**Os comandos mais comuns no Linux para gerenciar usuários e permissões são:**

**Usuários e Grupos:**

`useradd nome_usuario` - Cria um novo usuário

`userdel nome_usuario` - Apaga um usuário existente

`usermod opções nome_usuario` - Modifica as configurações de um usuário existente

`passwd nome_usuario` - Altera a senha de um usuário

`groupadd nome_grupo` - Cria um novo grupo

`groupdel nome_grupo` - Apaga um grupo existente

`groupmod opções nome_grupo` - Modifica as configurações de um grupo existente

`adduser nome_usuario nome_grupo` - Adiciona um usuário a um grupo

`deluser nome_usuario nome_grupo` - Remove um usuário de um grupo

**Permissões e Proprietários de Arquivos e Diretórios:**

`chmod permissões arquivo` - Modifica as permissões de um arquivo ou diretório. As permissões podem ser especificadas em notação octal (por exemplo, 755) ou usando letras (por exemplo, u+x)

`chown proprietário[:grupo] arquivo` - Altera o proprietário (e opcionalmente o grupo) de um arquivo ou diretório

`chgrp grupo arquivo` - Altera o grupo de um arquivo ou diretório

`ls -l` - Lista os arquivos/diretórios em um diretório junto com as permissões, proprietário, e grupo

Lembre-se de que a maioria desses comandos requer privilégios de root, então eles precisam ser executados com sudo (no Ubuntu e similares) ou como usuário root (em sistemas Red Hat e similares)
