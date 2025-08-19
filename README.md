Algoritmo: contador_passageiros

Este algoritmo calcula a quantidade de usuários (Entredas) que circulam em ônibus com mais de uma linha por viagem, realizadas nos horários que o usuário decidir analizar. Ele exibe em tela:

 - A quantidade total de usuários
 - Informações úteis para análise de fluxo: Linhas mais utilizadas e menos ultizada e acordo com o fuxo.

Sua finalidade seria de auxiliar, junto a um kit de cameras e "swith", na interpretação de dados pelos quais indicam os usos mais e menos frequentes, linhas de onibûs defasadas, horários inutilizados entre outros que poderam ser adicionadas poseriormente.

Esse algoritmo foi desenvolvido para Python, com o uso de bibliotecas externas, o proprio detecta um arquivo ja com nome especifico para interpretar os dados que, de acordo com o cliente, são levantados pelas cameras dos onibus, a 'IDE' utilizida foi o programa Visual Code.

Abra o projeto no Visual Studio Code: coloque o arquivo .csv na raiz do projeto (com o nome esperado pelo script "out") clicando com o botão direito do mouse e ir em "Abrir com o VSCode" selecionando o arquivo main.py junto ou abrindo a propria pasta identificada como projeto_contador_passageioros. 

Resumidamente a infraestrutura de dados veem de um arquivo ".csv", em que no mesmo indica a seguinte linha exeplo: "número do onibûs/linha","entrada de passageiros" ':' ("saida de passageiros").
Possui dentro do algoritmo uma função "def" que analiza o arquivo, redigita as linhas com os dados de maneira em que o programa consiga interpretar, possui também mensgens de avisos para informar o usuário a falta de sucesso com o arquivo.

Fluxograma (13/08):
![Alt text](https://github.com/Vitor-ALucn/contador_passageiros/blob/main/Contador%20de%20Passageiros.png)

Código-fonte (18/08):

    from collections import defaultdict

    def analisar_dados_onibus():
    try:
        with open('out.csv', 'r', encoding='utf-8') as arquivo:
            linhas = arquivo.readlines()
    except FileNotFoundError:
        print("Arquivo 'out.csv' não encontrado!")
        return

    capacidade_maxima = 50
    dados_onibus = defaultdict(list)

    for linha in linhas:
        linha = linha.strip()
        if not linha:
            continue

        partes = linha.split(',')
        numero_linha = partes[0]

        for item in partes[1:]:
            if ':' in item:
                try:
                    entrada, saida = map(int, item.split(':'))
                    dados_onibus[numero_linha].append((entrada, saida))
                except ValueError:
                    print(f"Erro ao processar parada: {item}")
                    continue

    resultados = []

    for linha, paradas in dados_onibus.items():
        total_entrada = sum(e for e, _ in paradas)
        total_saida = sum(s for _, s in paradas)
        fluxo_liquido = total_entrada - total_saida

        lotacao_atual = 0
        lotacao_maxima = 0

        for entrada, saida in paradas:
            lotacao_atual += entrada - saida
            lotacao_atual = max(0, min(lotacao_atual, capacidade_maxima))
            lotacao_maxima = max(lotacao_maxima, lotacao_atual)

        porcentagem_lotacao = (lotacao_maxima / capacidade_maxima) * 100

        resultados.append({
            'linha': linha,
            'total_entrada': total_entrada,
            'total_saida': total_saida,
            'fluxo_liquido': fluxo_liquido,
            'lotacao_maxima': lotacao_maxima,
            'porcentagem_lotacao': porcentagem_lotacao,
            'numero_paradas': len(paradas)
        })

    if not resultados:
        print("Nenhum dado válido encontrado no arquivo.")
        return

    resultados.sort(key=lambda x: x['total_entrada'], reverse=True)
    linha_menos_utilizada = min(resultados, key=lambda x: x['numero_paradas'])
    linha_menor_fluxo = min(resultados, key=lambda x: x['total_entrada'])

    print("=" * 30)
    print("ANÁLISE DE LINHAS DE ÔNIBUS".center(30))
    print("=" * 30)
    print(f"{'Linha':<10} {'Usuários':<10} {'Paradas':<15}")
    print("-" * 30)

    for r in resultados:
        print(f"{r['linha']:<10} {r['total_entrada']:<10} {r['numero_paradas']:<10}")

    print("-" * 30)
    print("\nLINHAS COM MAIOR VOLUME DE PASSAGEIROS:")
    for i, r in enumerate(resultados[:3]):
        print(f"{i+1}º Lugar: Linha {r['linha']} - {r['total_entrada']} passageiros")

    print(f"\nLINHA COM MENOR FLUXO:\nLinha {linha_menor_fluxo['linha']} - {linha_menor_fluxo['total_entrada']} passageiros")
    print(f"\nLINHA MENOS UTILIZADA:\nLinha {linha_menos_utilizada['linha']} - {linha_menos_utilizada['numero_paradas']} paradas")
    print(f"\nCAPACIDADE MÁXIMA DOS ÔNIBUS: {capacidade_maxima} passageiros")

    # Executar
    if __name__ == "__main__":
    analisar_dados_onibus()
