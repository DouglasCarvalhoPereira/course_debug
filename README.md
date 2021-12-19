# Curso Troubleshooting and Debugging Techniques

Depuração de Solução de Problemas

### Solução de Problemas
É o processo de identificação, análise e resolução de problemas.
É usado solução de problemas no sistema executando o aplicativo.

### Debugging
É o processo de identificação, análise e remoção de bugs em um sistema
É usado Debugging quando estamos resolvendo o código real do APP


Passos para soluções eficientes:

1. Reunir o máximo de informações necessários sobre o estado atual, qual a questão, quando acontece e quais as consequências.
2. Encontrar a RAIZ DO PROBLEMAS(Geralmente o mais difícil)
3. Realizar correção necessária

## Ferramentas

Strace - Ferramenta de rastreamento profundo do que o programa está fazendo.

## Ler arquivos de Log SEMPRE

### Linux
/var/log/syslog
- Logs específicos do usuário
.xsession-errors

### MacOs
/Library/Logs

### Windows
Event Viewer

## Etapas do processo:

#### Obter informações
#### Encontrar a Raiz do Problema
#### Eimplementar Correções


# Monitoring Tools
### Check out the following links for more information:
- https://docs.microsoft.com/en-us/sysinternals/downloads/procmon 
- http://www.brendangregg.com/linuxperf.html
- http://brendangregg.com/usemethod.html

Activity Monitor in Mac:

Performance Monitor on Windows

- https://www.digitalcitizen.life/how-use-resource-monitor-windows-7
- https://docs.microsoft.com/en-us/sysinternals/downloads/process-explorer
- https://en.wikipedia.org/wiki/Cache_(computing)
- https://www.reddit.com/r/linux/comments/d7hx2c/why_nice_levels_are_a_placebo_and_have_been_for_a/


### Analisar a velocidade de um script

Um sistemas está muito lento por exemplo envio de emails, armazenamento e gerenciamento de arquivos automaticamente e etc.

Vamos analisar o tempo de execução desse sistema e descobrir o significa lento, ou seja qual parte do sistema está lenta.

Como a lentidão é no "Envio" dos emails, trata-se de um problema no script, então análisamos o código python e executamos com parâmetros teste para testar a velocidade do software.

##### Tolls

- time

Ex.: 
$ time ./send_reminders.py "2020-01-13|Example|teste1"

Retorno do sistema
1. real 0m0.129s
    - Quantidade de tempo real que levou para executar o comando(Wall-clock time).

2. user 0m0.068s
    - Tempo gasto executando operações no espaço do usuário.

3. sys  0m0.013s
    - Tempo gasto fazendo operações no nível do sistema(Valor pode ser enviesado por ter outros apps em execução no computador).

### Para detalhar melhor o problema ou o que está deixando mais lento o sistema, usaremos o PROFILER

- profile3

###### command

$ pprofile3 -f callgrind -o profile.out ./send_reminders.py "2020-01-13|Example|teste1"

Foi gerado um arquivo com informações que podemos abrir em qualquer ferramenta com suporte ao formato grand call.

Nesse caso usaremos o ###### kcachegrind

Após identificar o ponto que consome mais tempo otimizamos o código.

### Simultaneadade para otimizar o funcionamento do código

Simultaneidade para melhorar nossos programas. Mais detalhes sobre as diferentes maneiras de usar a simultaneidade em Python.

Links a seguir para obter mais informações:

https://realpython.com/python-concurrency/

https://hackernoon.com/threaded-asynchronous-magic-and-how-to-wield-it-bba9ed602c32

Multiprocessameto por CPU

### Verificar saúde da memória RAM memtest86

Para verificar a memório RAM do computador podemos usar o memtest86 que irá procurar por erros.
Deve ser executado ao inciar o sistema operacional a fim de de ter acesso a toda memória disponível 
e verificar se os dados gravados na memório são os mesmos de quando tenta le-lo de novo.

### Acompanhar o que um programa está fazendo

Quando não tivermos acesso aos logs do sistema ou identificar o erro podemos monitorar o que a aplicação está fazendo por exemplo abrir um diretório, se conectar com a rede ou deletar algo usando as ferramentas abaixo.

###### Linux
 - strace

###### MacOS
 - dtruss

###### Linux
 - Process Monitor


### Escrever script que pré-processa os dados e atua na/como PROXY

##### - wrapper

Função ou programa que fornece uma camada de compatibilidade entre duas funções ou programas para que eles possam trabalhar bem juntos.

Usado quando os formatos de entrada e saída não correspondem.

###### Watchdog

Script que verifica o funcionamento do programa com frequência e caso de algum erro que o pare o própio script o reinica para garantir o funcionamento do serviço.


#### Identificar problemas no código relacionados a memória e outros no LINUX E MACOS

##### valgrind

## No wWindows

podemos o Dr Memory

# DEPURADOR PYTHON DE LINHA DE COMANDO

### pdb3