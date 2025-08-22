# ***Algoritmo: contador_passageiros***

##### Este algoritmo calcula a quantidade de usuários (Entredas) que circulam em ônibus com mais de uma linha por viagem, realizadas nos horários que o usuário decidir analizar. Ele exibe em tela:

 - A quantidade total de usuários
 - Informações úteis para análise de fluxo: Linhas mais utilizadas e menos ultizada e acordo com o fuxo.

### Justificativa
Sua finalidade seria de auxiliar, junto a um kit de cameras e "swith", na interpretação de dados pelos quais indicam os usos mais e menos frequentes, linhas de onibûs defasadas, horários inutilizados entre outros que poderam ser adicionadas poseriormente.

Esse algoritmo foi desenvolvido para Python, com o uso de bibliotecas externas, o proprio detecta um arquivo ja com nome especifico para interpretar os dados que, de acordo com o cliente, são levantados pelas cameras dos onibus, a 'IDE' utilizida foi o programa Visual Code.

### Execução
Abra o projeto no Visual Studio Code: coloque o arquivo .csv na raiz do projeto (com o nome esperado pelo script "out") clicando com o botão direito do mouse e ir em "Abrir com o VSCode" selecionando o arquivo main.py junto ou abrindo a propria pasta identificada como projeto_contador_passageioros. 

### Infraestrutura
Resumidamente a infraestrutura de dados veem de um arquivo ".csv", em que no mesmo indica a seguinte linha exeplo: "número do onibûs/linha","entrada de passageiros" ':' ("saida de passageiros").
Possui dentro do algoritmo uma função "def" que analiza o arquivo, redigita as linhas com os dados de maneira em que o programa consiga interpretar, possui também mensgens de avisos para informar o usuário a falta de sucesso com o arquivo.

### Fluxograma
![Fluxograma do projeto](https://github.com/Vitor-ALucn/contador_passageiros/blob/main/Algoritmo%20contador%20(1).jpeg)

Autoria de Vitor Augusto L. ]|[
Software do fluxograma: lucid.app ]|[
Software da apresentação(.pdf): Canva.com
