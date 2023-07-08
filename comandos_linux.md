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
