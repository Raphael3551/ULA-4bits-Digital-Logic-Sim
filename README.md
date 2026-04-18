# ULA de 4 Bits - Digital Logic Sim

Este projeto apresenta uma Unidade Lógica e Aritmética (ULA) completa, capaz de realizar operações de soma, subtração, multiplicação e divisão com 4 bits.

## Como baixar e executar
1. Obtenha o simulador: Baixe e instale [**Digital Logic Sim**](https://sebastian.itch.io/digital-logic-sim).
2. Baixe o Projeto: Clique no botão verde Code (topo da página) e selecione Download ZIP. Após o download, extraia a pasta.
3. Localize a Pasta de Projetos:

    Pressione as teclas Win + R no seu teclado.

    Digite %appdata% e aperte Enter.

    Agora, navegue para o seguinte caminho (volte uma pasta para AppData ou suba o nível):
    ...\AppData\LocalLow\Sebastian Lague\Digital-Logic-Sim\Projects
4. Instalação: Copie a pasta ULA (que você extraiu) e cole-a dentro da pasta Projects mencionada acima.
5. Execução: Abra o simulador e o projeto aparecerá na lista de seleção após clicar em "Open Project".

## Explicação do Funcionamento

### Vídeo explicativo:

### Somador (Full Adder)

O somador completo é construído utilizando portas XOR, AND e OR. Ele processa três entradas (Operandos A, B e o Carry-in) e gera duas saídas (Soma e Carry-out). Na pasta OPERADORES 1BIT, você pode visualizar a lógica interna; os modelos de 4 e 8 bits foram estruturados através da cascata (replicação) deste módulo básico.

### Subtrator (Via Complemento de 2)

A lógica de subtração é implementada sobre a estrutura do somador. Para subtrair, aplica-se a negação (Porta NOT) no segundo operando e soma-se 1 ao resultado (lógica de Complemento de 2).

> Implementação: Utiliza-se um Multiplexador (MUX) na entrada B. Quando a seleção é ativada (1), o MUX envia o valor negado ao somador e injeta simultaneamente o bit 1 no Carry-in inicial, realizando a operação A−B.

### Multiplicador (Shift and Add)

A multiplicação baseia-se na lógica de deslocamento e soma. Cada bit do segundo operando é comparado individualmente com o primeiro valor. Caso o bit seja 1, o primeiro operando é deslocado para a esquerda de acordo com a posição do bit (peso posicional) e somado aos resultados parciais. O módulo realiza a conversão de barramentos de 4 bits para 8 bits para comportar o produto final sem perda de dados.

### Divisor (Restoring Division)

O divisor utiliza um algoritmo iterativo de deslocamento. O dividendo é percorrido do bit mais significativo para o menos significativo, formando um valor parcial que é comparado ao divisor.

> Se o valor parcial for maior ou igual ao divisor, o bit correspondente do quociente é definido como 1 e subtrai-se o divisor do valor parcial.
> Caso contrário, o bit do quociente é 0.

> Este processo se repete por 4 ciclos até que todos os bits sejam processados, resultando no quociente e no resto.

### Unidade Lógica e Aritmética (ULA)

A ULA é o módulo central que integra os quatro circuitos anteriores. Ela recebe dois operandos de 4 bits e utiliza um conjunto de multiplexadores para selecionar qual operação será enviada para a saída final.

A seleção é feita através de 2 bits de controle (Sel), conforme a tabela abaixo:
| Bit (S1 S0) | Operação |
| :---: | :--- |
| 00 | Adição |
| 01 | Subtração |
| 10 | Multiplicação |
| 11 | Divisão |

## Créditos
Desenvolvido por: Raphael Henrique Dos Reis Gomes
Disciplina: SSC0955-Introducao a Sistemas Computacionais - 2026
