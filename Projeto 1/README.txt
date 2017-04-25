/*************************************************************************

   >>> MAC0329 (Álgebra Booleana e Circuitos)

   Grupo:
    > Antonio Carlos Santos de Lima - nº USP:  8515986
    > Gustavo Chicato Wandeur       - nº USP:  7557797
    > Victor Hugo Miranda Pinto     - nº USP: 10297720

*************************************************************************/

*******************************
    DESCRIÇÃO DOS CIRCUITOS
*******************************

=========
   ULA
=========

ENTRADA:
- Números A e B, de 8 bits;
- Dois bits, s1 e s0, representando o seletor S da operação.

SAÍDA:
- Resultado R, também um número de 8 bits, originado de uma operação entre A e B;
- Um pino o0 para indicar se houve a ocorrência de overlow;
- Três pinos o1, o2 e o3 para indicar os possíveis resultados da comparação.

DESCRIÇÃO:
   É a "interface" do programa, que recebe os valores e a operação desejada
e devolve o resultado final.

============
    SOMA
============

ENTRADA:
- Números A e B, de 8 bits;

SAÍDA:
- Valor R = A + B;
- Indicação do overflow.

DESCRIÇÂO:
   Recebe um carry inicial c0, constante e zero. Soma os bits correspondentes
por meio do circuito somador de dois bits. O bit resultante vai para a saída
e o carry entra no próximo somador. O overflow é verificado por meio de um XOR
entre os dois últimos carrys (se forem diferentes, então ocorreu overflow).

-------------------------
   (SOMADOR DE 2 BITS)
-------------------------

ENTRADA:
- 2 bits, a e b;
- 1 bit cin (carry in).

SAÍDA:
- 1 bit s = a + b;
- 1 bit cout (carry out)

DESCRIÇÂO:
   Calcula as saídas pelas seguintes expressões booleanas:
       cout = {a^b)cin + ab
          s = (a^b)^cin

=================
    SUBTRAÇÃO
=================

ENTRADA:
- Números A e B, de 8 bits;

SAÍDA:
- Valor R = A - B;
- Indicação do overflow.

DESCRIÇÃO:
   A subtração é feita como soma de A mais o complemento de dois de B, ou seja:
                        A - B = A + (-B)
   Ocorre overflow se naturalmente ocorrer overflow na soma (indicado pelo
próprio subcircuito).

---------------------------
   (COMPLEMENTO DE DOIS)
---------------------------

ENTRADA:
- Um número A, de 8 bits;

SAÍDA:
- O complemento de dois de A, ou seja, -A;

DESCRIÇÃO:
   Usa-se o método padrão para calcular o complemento de dois de um número:
cada bit é trocado (negado) e a esse resultado soma-se 1.

================
   COMPARADOR
================

ENTRADA:
- Um número A, de 8 bits.

SAÍDA:
- Bit representando o resultado da comparação com zero.
    o1 : se A  < 0
    o2 : se A == 0
    o3 : se A  > 0

DESCRIÇÃO:
    o1 ocorre se o bit mais significativo for 1 (ou seja, nº negativo);
    o2 ocorre se todos os bits forem 0 (zero);
    o3 ocorre se o2 não ocorrer e se o bit mais significativo for 0 (ou seja, nº positivo).
