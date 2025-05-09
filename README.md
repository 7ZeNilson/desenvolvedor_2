DESENVOLVEDOR 2

# 1  Valor da variável SOMA

INDICE = 13
SOMA = 0
K = 0

while K < INDICE:
    K = K + 1
    SOMA = SOMA + K

print("Resposta:", SOMA)

Resposta: 91

# 2 Sequência de Fibonacci

def fibonacci(numero):
    """
    Calcula a sequência de Fibonacci e verifica se um número pertence a ela.

    Args:
      numero: O número a ser verificado.

    Returns:
      Uma string informando se o número pertence ou não à sequência.
    """

    a, b = 0, 1
    sequencia = [a, b]

    while b < numero:
        a, b = b, a + b
        sequencia.append(b)

    if numero in sequencia:
        return f"Resposta: O número {numero} pertence à sequência de Fibonacci: {sequencia}"
    else:
        return f"Resposta: O número {numero} não pertence à sequência de Fibonacci: {sequencia}"

# Exemplo de uso:
numero_para_verificar = 21 # Você pode alterar este número
resultado = fibonacci(numero_para_verificar)
print(resultado)

Resposta: O número 21 pertence à sequência de Fibonacci: [0, 1, 1, 2, 3, 5, 8, 13, 21]


# 3 Análise de Faturamento Diário
import json

def analisar_faturamento(dados):
    """
    Calcula o menor, maior faturamento e dias acima da média.

    Args:
      dados: Uma lista de dicionários contendo 'dia' e 'valor'.

    Returns:
      Um dicionário com os resultados.
    """

    faturamentos_validos = [dia['valor'] for dia in dados if dia['valor'] > 0]

    if not faturamentos_validos:
        return "Resposta: Não há dados de faturamento válidos para calcular."

    menor_faturamento = min(faturamentos_validos)
    maior_faturamento = max(faturamentos_validos)
    media_mensal = sum(faturamentos_validos) / len(faturamentos_validos)
    dias_acima_da_media = sum(1 for faturamento in faturamentos_validos if faturamento > media_mensal)

    return {
        "menor_faturamento": f"Resposta: O menor faturamento foi R$ {menor_faturamento:.2f}",
        "maior_faturamento": f"Resposta: O maior faturamento foi R$ {maior_faturamento:.2f}",
        "dias_acima_da_media": f"Resposta: {dias_acima_da_media} dias tiveram faturamento acima da média mensal de R$ {media_mensal:.2f}"
    }

# Carregar os dados do arquivo JSON
with open('dados.json', 'r') as f:
    dados_faturamento = json.load(f)

resultados = analisar_faturamento(dados_faturamento)
print(resultados)

{'menor_faturamento': 'Resposta: O menor faturamento foi R$ 373.78', 'maior_faturamento': 'Resposta: O maior faturamento foi R$ 48924.24', 'dias_acima_da_media': 'Resposta: 10 dias tiveram faturamento acima da média mensal de R$ 20865.37'}


# 4 Percentual de Representação por Estado

def calcular_percentual_faturamento(faturamento_por_estado):
    """
    Calcula o percentual de representação de cada estado no faturamento total.

    Args:
      faturamento_por_estado: Um dicionário com o faturamento por estado.

    Returns:
      Um dicionário com os percentuais de cada estado.
    """

    total_faturamento = sum(faturamento_por_estado.values())
    percentuais = {}

    for estado, faturamento in faturamento_por_estado.items():
        percentual = (faturamento / total_faturamento) * 100
        percentuais[estado] = f"Resposta: {estado}: {percentual:.2f}%"

    return percentuais

# Dados de faturamento
faturamento_estado = {
    "SP": 67836.43,
    "RJ": 36678.66,
    "MG": 29229.88,
    "ES": 27165.48,
    "Outros": 19849.53
}

percentuais_estado = calcular_percentual_faturamento(faturamento_estado)
for resultado in percentuais_estado.values():
  print(resultado)

Resposta: SP: 37.53%
Resposta: RJ: 20.29%
Resposta: MG: 16.17%
Resposta: ES: 15.03%
Resposta: Outros: 10.98%

# 5 Inverter String

def inverter_string(texto):
    """
    Inverte os caracteres de uma string sem usar funções prontas como reverse.

    Args:
      texto: A string a ser invertida.

    Returns:
      A string invertida.
    """

    texto_invertido = ""
    for i in range(len(texto) - 1, -1, -1):
        texto_invertido += texto[i]
    return f"Resposta: {texto_invertido}"

# Exemplo de uso:
minha_string = "Hello World" # Você pode alterar esta string
string_invertida = inverter_string(minha_string)
print(string_invertida)

Resposta: dlroW olleH


