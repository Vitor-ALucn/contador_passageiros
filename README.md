Algoritmo: contador_passageiros

Algoritmo que calcule a quantidade de usuários que circulam no ônibus com mais de uma linha por viagens, realizadas nos horários de pico, mostra a porcentagem de lotação, quantidade de usúarios tudo isso sendo exibido em tela.

Sua finalidade seria de auxiliar, junto a um kit de cameras e "swith", na interpretação de dados pelos quais indicam os usos mais e menos frequentes, linhas de onubûs defasadas, horários inutilizados entre outros. 

Esse algoritmo foi desenvolvido para Python, sem o uso de bibliotecas externas, o proprio detecta um arquivo ja com nome especifico para interpretar os dados que, de acordo com o cliente, são levantados pelas cameras dos onibus, a 'IDE' utilizida foi o programa Visual Code.

Resumidamente a infraestrutura de dados veem de um arquivo ".txt", em que no mesmo indica a seguinte linha exeplo: ["número do onibûs/linha",("entrada de passageiros") ':' ("saida de passageiros")]  

Fluxograma (13/08)

1° - O algoritmo tem como inicio uma função 'with' para abrir o arquivo com as seguintes informações: Número da linha, n° de vezes em que ela é executado, entradas e saídas de passageiros.
2° - A proxima função ira separar dentro de vetores, usando um 'loop', o número da linha com passageiros e paradas com entra e saídas.
3 ° - Outra funcição vai classificar por horários o fluxo de uso da linha/onibûs retornando como porcentagem.
4° - 
