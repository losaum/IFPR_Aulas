# Introdução ao Linux e Bash



## Comandos Básicos


### Interpretadores

Um *shell* é uma interface de comunicação com o sistema operacional, e para que possa ser utilizado é necessário a utilização de um **interpretador**. Os interpretadores definirão qual sintaxe será utilizada, bem como o uso de variáveis ou recursos auxiliares, como autocomplete, cores, dentre outros.

Interpretadores bastante conhecidos são bash, bsh, ksh, e diversos outros.

Neste material, utilizaremos o interpretador GNU Bourne-Again SHell (`bash`)

### Comandos e parâmetros

Cada interpretador pode possuir comandos específicos dele, sem a necessidade de nenhum *sofware* externo. Ou seja, comandos internos a ele que não dependem de instalação ou configuração do ambiente.

A sintaxe para execução de um comando é 

```
<comando> <parâmetros>
```

O separador de parâmetros é o ` ` (espaço). 

**Exemplos**
```
ls-l #sem espaço, resultado em erro
ls -l #com espaço, executando o comando ls com o parâmetro -l
ls         -l #múltiplos espaços são convertidos em um único espaço.
```

Há diversos parâmetros padrão, e incluídos na grande maioria dos comandos, como ajuda (`-h`) ou versão (`-v`).

Grande parte dos parâmetros segue o padrão de um hífen (`-`) é seguido de um caractere, enquanto dois hífens (`--`) são seguidos de mais de um caractere.

**Exemplos**
```
wget -h
wget --help
java --version
```
## Manipulação de arquivos e dirétórios

### pwd

Informa qual é o diretório atual em que o interpretador está sendo executado.

```
pwd
```

### ls

Lista os arquivos e diretórios presentes no diretório atual. Por padrão, o comando `ls` imprimirá o nome de todos os arquivos e diretórios apenas. 

**Exemplo**

```
ls
```

O comando `ls` pode receber diferentes parâmetros.

**Parâmetros**

- `-1` : lista o conteúdo em uma única coluna
- `-l` : apresenta detalhes, como permissões, datas de acesso e outros
- `-a` : (*all*) mostra também arquivos e diretórios ocultos
- `-s` : (*size*) mostra o tamanho dos arquivos
- `-h` : (*human*) apresenta o tamanho dos arquivos utilizando múltiplos (KiB, MiB, GiB)
- `-R` : recursivo. abre e lista os arquivos em todos todos os diretórios e seus subdiretórios

### cd

*Change directory*. Com ele podemos alterar o diretório atual, passando o diretório que queremos acessar como parâmetro.

**Parâmetros**

- "diretorio" : diretório a ser aberto, que será atualizado como diretório atual
- "" : executar `cd` sem parâmetros leva ao diretório padrão. Comumente é a *home* do usuário (`/home/usuario/`)
- \- :  diretório anterior

Os parâmetros para o comando `cd` podem ser:
- um caminho **absoluto**, a partir da raíz do sistema
- um caminho **relativo**, a partir do diretório atual

Nos sistemas de arquivos, cada diretório possui dois *links* especiais:
- `..` : atalho para o diretório imediatamente superior (diretório pai)
- `.` : atalho para o próprio diretório  


Exemplos  
```
cd trabalhos #Abre o diretório trabalhos.
cd /home/aluno/Documentos #Abre o diretório Documentos, utilizando o caminho abosoluto
cd .. #Entra no diretório superior
cd ../trabalhos/Algoritmos #Volta ao diretório pai, e a partir dele acessa o diretório trabalhos, e abre o diretório Algoritmos
```

### mkdir

Cria um ou mais novos diretórios.

**Parâmetros**  
- "nome" : nome do diretório a ser criado. Diversos nomes podem ser passados
- `-p` : cria diretórios e subdiretórios, demarcados com `/` e `{}`.

**Exemplos**  

```
mkdir sistemas #cria o diretório sistemas
mkdir -p "faculdade/{disciplinas,documentos}" #cria o diretório faculdade, que possui 2 subdiretórios: disciplinas e documentos
```

Cuidado! Caso sejam utilizados nomes com espaços, este deve ser tratado, utilizando `\ ` ou então colocando o nome entre aspas.

**Exemplos**
- Ao executar:  
 `mkdir sistemas operacionais`  
 é entendido que são passados 2 parâmetros, as palavras `sistemas` e `operacionais`, e portando 2 diretórios serão criados.  
 Para criar um único diretório:
 ```
 mkdir "sistemas operacionais" # ou
 mkdir sistemas\ operacionais
 ```


### touch

Você pode criar um novo arquivo por meio do comando `touch` seguido pelo nome do arquivo que deseja criar:
```
touch hello_world.txt 
```

Você pode editar arquivos usando qualquer editor de texto gráfico. Se preferir editar um arquivo diretamente da linha de comando, precisará usar um editor de linha de comando, como vim, emacs ou nano. Muitas distribuições vêm com um ou mais desses programas instalados, mas você sempre pode instalar esses programas seguindo as instruções de instalação.

Para editar o arquivo com seu método preferido de edição, basta executar o nome do programa seguido pelo nome do arquivo que você deseja editar: 

```
nano hello_world.txt 
```

### cp

Realiza a cópia de um ou mais arquivos. É necessário especificar o arquivo de origem e o diretório de destino, onde o arquivo será copiado. O diretório de destino deve existir!

**Exemplos**  
```
cp Hello.java trabalhos/algoritmos/ 
#Faz uma cópia do arquivo Hello.java, e salva a cópia dentro do diretório trabalhos/algoritmos
```

**Parâmetros**  
- `-r` : copia diretórios

### mv

Semelhante a `cp`, porém ao invés de criar uma cópia, move o próprio arquivo.

### rm

Deleta um arquivo, removendo-o do sistema de arquivos.

**Parâmetros**  

- `-r` : apaga diretórios

## Visualização de arquivos

### cat

Mostra o conteúdo do arquivo na saída padrão.

**Exemplos**  
```
cat Hello.java
```

### less

Mostra o conteúdo do arquivo, porém limita o conteúdo ao tamanho da tela. O usuário pode utilizar as setas &uarr; &darr; para navegação.

### head

Mostra as primeiras linhas do arquivo na saída padrão. Por padrão, são mostradas as primeiras 10 linhas.

**Parâmetros**  
- `-n x` : mostra as `x` primeiras linhas

**Exemplos**  
```bash
head Hello.java
head -n 5 Hello.java
```

### tail

Semelhante ao comando `head`, porém para as últimas linhas do arquivo. Por padrão, são mostradas as últimas 10 linhas.  

**Parâmetros**
- `-n x` : mostra as `x` últimas linhas
- `-f` : caso o arquivo seja atualizado, apresenta o novo conteúdo

**Exemplos**  
```bash
tail Hello.java
tail -n 5 Hello.java
tail -n 2 -f Hello.java
```

### grep
Filtra o conteúdo de um arquivo, mostrando apenas as partes que correspondem a determinados critério.

**Exemplos**
- Mostra apenas as linhas que contenham a palavra `print` do arquivo `Hello.java`
```
grep print Hello.java
```

Dica:
O comando `grep` é extremamente poderoso, e pode ser combinado com expressões regulares.


### wc

Obtém informações quantitativas sobre determinado arquivo.

**Parâmetros**  
- `-l` : quantidade de linhas
- `-c` : quantidade de caracteres
- `-w` : quantidade de palavras

**Exemplo**  
```
wc -l Hello.java
wc -c Hello.java
```

### diff
Aponta a diferença entre dois arquivos

**Exemplo**
```
diff Hello.java Hello_v2.java
```

## Mais comandos auxiliares

### echo

Apresenta uma mensagem na saída padrão.

```bash
echo "Boa noite pessoal
```

### seq

Gera uma sequência de valores.

**Exemplos**
```bash
seq 5 #valores de 1 a 5
seq 8 20 #valores de 8 a 20
seq -w 2 15 #valores de 2 a 15, mantendo a mesma quantidade de algarismos.
```

### clear

Limpa a tela, movendo o cursor para a linha inicial. Há um atalho para este comando: `ctrl+l`.

**Exemplo**  

```
clear
```

### exit

Encerra a sessão atual. Em sistemas gráficos, pode fechar a janela. Em sistemas sem janela, retorna para tela de login do usuário.

```
exit
```

### man

Acessa o manual referente ao sofware/comando, caso exista. Para sair, digite `q`.  

**Exemplos**  
```
man ls
man pwd
```

### history

Apresenta a lista de comandos digitados recentemente.

### alias

Permite criar um *alias* para uma sequência digitada. O *alias* criado possui validade durante a sessão. Pode sobrescrever um comando já existente ou criar um novo.

**Exemplos**

- ls com opções
```
alias ls="ls -l -a"
ls
```

- ativando ambientes virtuais Python

```
alias py="source /home/usuario/.env/bin/activate" #alias para o comando que carrega o ambiente python
py #ativa o ambiente python
```

### unalias

Desfaz um *alias* criado previamente.

**Exemplos**  

```
unalias ls
unalias py
```

### which

Informa o caminho para o *software* responsável pelo comando.

**Exemplos**  

```
which ls
which pwd
which cat
which less
```

O `which` retorna vazio para comandos *built-in* do bash, ou seja comandos que são executados pelo próprio interpretador, sem a necessidade de *softwares* externos. Exemplos: `cd`, `for`, `if`.

### sleep

Aguarda por determinado tempo. As unidades de tempo são `s`, `m`, `h` e `d` para segundos, minutos, horas e dias, respectivamente.  

**Exemplos**  
```
sleep 5s  #aguarda 5 segundos
sleep 30m #aguarda 30 minutos
sleep 20h #aguarda 20 horas
sleep 8d  #aguarda 8 dias
```

### date

Mostra a data e hora corrente use o comando `date` 
```
date
```

## Usando pipes e operadores de redirecionamento

Um pipe '|' redireciona a saída de um comando como entrada para outro comando. Por exemplo, lhscmd | rhscmd direcionaria a saída de lhscmd para rhscmd. Os pipes podem ser usados de várias maneiras para realizar tarefas rapidamente por meio da linha de comando. Abaixo estão apenas alguns exemplos simples de como os pipes podem ser usados.
Imagine que você deseja classificar rapidamente o conteúdo de um arquivo. Veja o exemplo de fruits.txt abaixo:

```
cat fruits.txt 
```
**Saída:**
```
Orange 

Banana 

Apple 

Pear 

Plum 

Kiwi 

Strawberry 

Peach
```

Você pode classificar essa lista rapidamente usando um pipe:

```
cat fruits.txt | sort 
```
**Saída:**
```
Aple 

Banana 

Kiwi 

Orange 

Peach 

Pear 

Plum 

Strawberry
Peach
```
Por padrão, a saída do comando `cat` é enviada para a saída padrão; no entanto, o '|' nos permite redirecionar a saída como a entrada para outro comando, `sort`.

Outro caso de uso é a pesquisa. Você pode usar `grep`, que é um comando útil que pesquisa a entrada de uma cadeia de caracteres de pesquisa específica.

Mostra as linhas em que ocorre uma expressão dentro do arquivo
```
cat fruits.txt | grep P 
``` 
**Saída:**
```
Pear 

Plum 

Peach
```

Você também pode usar operadores de redirecionamento como '>' para passar a saída para um arquivo ou fluxo. Por exemplo, se você quiser criar um novo arquivo .txt com o conteúdo classificado de fruit.txt:
```
cat fruits.txt | sort > sorted_fruit.txt 

``` 
**Saída:**
```
Apple 

Banana 

Kiwi 

Orange 

Peach 

Pear 

Plum 

Strawberry
```

Por padrão, a saída do comando de classificação é enviada para a saída padrão; no entanto, o operador '>' nos permite redirecionar a saída para um novo arquivo chamado sorted_fruits.txt.

Você pode usar pipes e operadores de redirecionamento de várias maneiras interessantes para concluir tarefas com mais eficiência diretamente da linha de comando.

## Instalando e atualizando software

Você pode instalar e atualizar programas de software diretamente da linha de comando usando o gerenciador de pacotes preferencial para a distribuição que você está executando.

No Ubuntu, por exemplo, primeiro atualize a lista de softwares disponíveis executando `sudo apt update`. Em seguida, você pode obter software diretamente usando o comando `sudo apt-get install` seguido pelo nome do programa que deseja instalar:
```
sudo apt-get install <app_name> 
```
Para atualizar os programas que já foram instalados, você pode executar:
```
sudo apt update && sudo apt upgrade
```


## Diretórios Principais

Os diretórios principais, além de outros, com seu conteúdo estão listados abaixo:
- /etc - Arquivos para administração do sistema.
- /bin - Comandos UNIX mais comumente usados.
- /usr - Todas as contas de usuários e alguns comandos.
- /dev - Arquivos de dispositivos de entrada e saída.
- /lib - Arquivos bibliotecas para programação em C.
- /tmp - Armazenamento de arquivos temporários.
- /mmt - Montagem de discos e periféricos.
- /sbin - Diretório usado na inicialização do sistema. Demais pacotes para a administração do
sistema devem #car em /usr/sbin ou /usr/local/sbin.
- /var - Diretório que contém arquivos variáveis, tais como spool (filas de e-mail, crontab, impressão)
e logs. Este diretório existe para que os arquivos que necessitem ser modificados fiquem nele e não no /usr.
- /home - Contém os diretórios pessoais dos usuários.
- /root - É o diretório que contém os arquivos do administrador (seu home ). Porém alguns sistemas Unix-like utilizam /home/root.
