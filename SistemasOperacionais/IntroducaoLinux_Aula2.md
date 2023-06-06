# Sistema
Comandos relaciondos ao sistema operacional.

## Comandos para obter informações sobre Usuários

### who

Exibe informações sobre os usuários logados.

**Parâmetros**
- '-m' : Informações delogin do próprio usuário.
- '-H' : Mostra um cabeçalho;
- '-a' : Diversas informações sobre o sistema e usuários

```
who -a
```

### id

Este comando retorna os identificadores do usuário; login e os grupos a que pertence.

```
id 
```

### finger

O comando finger pesquisa e exibe informações sobre os usuários do sistema.

```
finger

finger Aluno
```

### chfn

Para alterar as informaçãoes do usuário no sistema.

```
chfn
```

### groups

Informa os grupos que o usuário pertence.

```
groups # grupos que eu pertenço

groups aluno # grupos que o usuário aluno pertence
```


## Armazenamento

### du

Apresenta o espaço de armazenamento utilizado pelo diretório atual, ou pelos diretórios passados por parâmetro.

**Parâmetros**
- '-m' : apresenta o tamanho em MiB (MebiBytes)
- '-h' : apresenta o tamanho em múltiplos (KiB, MiB, GiB)

## df 

Apresenta a quantidade de armazenamento utilizada e disponível em cada sistema de arquivos (disk free).



## Sistema

### uname

Obtém informações sistema operacional.

**Parâmetros**  

- `-a | --all` : apresenta todas as informações
- `-v | --kernel-version`: versão do *kernel*
- `-s | --kernel-name`: nome do *kernel*
- `-i | --hardware-platform` : arquitetura utilizada
- `-o | --operating-system` : sistema operacional

### free

Indica a quantidade de memória presente no sistema.


### top

Mostra continuamente o status de cada processo que está  sendo executados no sistema. Para sair, deve ser pressionada a tecla `q`.

### ps

Lista os processos em execução no sistema

**Parâmetros**  

- `-e` : Apresenta linha de comando completa
- `-l`: Gera saída em formato longo
- `-a`: Inclui informações sobre processos pertencentes a todos os usuários
- `-u` : Produz saída orientada a usuário
- `-x` : Inclui processos não associados a terminais


**Exemplo**

```
ps -aux #lista todos processos que possuem um terminal (tty) associado e o usuário que originou o processo
```


### jobs 
Lista os processos suspensos e em segundo plano (blackground)

```
jobs
```


### bg
Coloca processos em segundo plano(blackground)

```
bg 2564  #bg [pid]
```
Outra forma simples de executar em background é adicionar o operador `&` no fim do comando, liberando assim o terminal.

```
cp filme.mov f: &
```

###  fg
Traz as tarefas que estão em segundo plano para o primeiro plano (foreground).

```
fg 2564  #fg [pid]
```


### kill

Envia um sinal a um processo. Em geral, é urilizado para cancelar um processo que "aparentemente travou". Somente o superusuário pode "matar" o processo de outros usuários.

```
kill -l # apresenta a lista de nomes de sinais aceitos pelo comando
```
 O sinal mais comum é `-9`, que indica para que o terminal seja finalizado. Se o parâmetro não for especificido, kill encia o sinal 15(terminate)

```
kill [-sinal]  [pid] 
```
O `pid` indica o process-id correspondente ao processo quew se deseja enviar um sinal

**Exemplos**
Solicita ao sistema operacional que o processo com PID 1025 seja finalizado.
```
kill -9 37493

kill -9 63772 45116 23465 # Encerra múltiplos processos

```

### kilall

Envia sinal a processos, porém utilizando o nome

**Exemplo**
```
killall chrome
```

### shutdown

Desliga o sistema. Permite que seja desligado dentro de determinado tempo.

**Exemplos**
```
shutdown -h now #desliga agora
shutdown -r now #reinicia agora
shutdown -h +90 #desligará o sistema em 90 minutos
shutdown -k #cancela um desligamento agendado previamente
```

### poweroff

Desliga o sistema.

```
poweroff
```
