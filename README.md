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


