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

`hostname` - Mostra na tela o nome do host

`gnome-calculator` - Através do bash é possível abrir aplicações que estejam instaladas na máquina apenas chamando o nome dela no terminal

`date ; echo 'Hello World'` - `;` serve para executar comandos sequênciais. Nesse caso executo o comando `date` e logo após o comando `echo`

`echo 'Hello World` - Imprime no terminal mensagens ou variáveis

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

`open nome_arquivo` - Abre o arquivo selecionado

`cp caminho_origem caminho_destino` - Copia o arquivo de origem para o destino

`cp -r caminho_origem caminho_destino` - Copia todo o diretório para o destino

`mv caminho_origem caminho_destino` - Move um arquivo ou diretório para o destino especificado. Esse comando também renomeia um arquivo ou diretório para o especificado