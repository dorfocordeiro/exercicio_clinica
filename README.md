# Análise de Atendimentos em Clínica Veterinária

## 📋 Descrição

Este exercício pratica consultas em MongoDB e análise de dados com pandas utilizando um dataset de 50 atendimentos realizados em uma clínica veterinária nas cidades de Assis, Ourinhos, Pompeia e Marília.

## 🎯 Objetivo

Realizar análises de atendimentos veterinários, calcular métricas financeiras e gerar um relatório estruturado salvo em MongoDB.

## 📊 Dados Disponíveis

Cada registro contém:
- **tutor**: Nome do tutor do animal
- **animal**: Tipo de animal (Cachorro, Gato, Ave, Coelho)
- **nome_pet**: Nome do animal
- **servico**: Tipo de serviço (Consulta, Vacinação, Banho, Exame, Cirurgia)
- **valor**: Valor do atendimento em reais
- **cidade**: Cidade onde foi realizado (Assis, Ourinhos, Pompeia, Marília)
- **data**: Data do atendimento
- **forma_pagamento**: Forma de pagamento (Pix, Cartão, Dinheiro)

## ✅ Atividades Realizadas

1. ✓ Inserir os 50 registros na coleção 'atendimentos'
2. ✓ Consultar atendimentos com valor entre 90 e 200 reais
3. ✓ Consultar atendimentos das 4 cidades principais
4. ✓ Converter resultados para DataFrame
5. ✓ Verificar valores nulos
6. ✓ Calcular faturamento total
7. ✓ Calcular faturamento por cidade
8. ✓ Calcular faturamento por serviço
9. ✓ Calcular ticket médio geral
10. ✓ Calcular ticket médio por cidade
11. ✓ Identificar o serviço mais lucrativo
12. ✓ Identificar a cidade com maior faturamento
13. ✓ Identificar os 3 maiores atendimentos

## 📈 Relatório Obrigatório

O relatório é gerado como dicionário Python com os seguintes campos:

```json
{
  "data_geracao": "2026-03-26T01:01:58.730950",
  "faturamento_total": 8895.0,
  "faturamento_por_cidade": {
    "Assis": 2220.0,
    "Marilia": 2275.0,
    "Ourinhos": 2380.0,
    "Pompeia": 2020.0
  },
  "faturamento_por_servico": {
    "Banho": 535.0,
    "Cirurgia": 3370.0,
    "Consulta": 2655.0,
    "Exame": 1505.0,
    "Vacinação": 830.0
  },
  "ticket_medio_geral": 177.9,
  "ticket_medio_por_cidade": {
    "Assis": 170.77,
    "Marilia": 189.58,
    "Ourinhos": 183.08,
    "Pompeia": 168.33
  },
  "servico_mais_lucrativo": "Cirurgia",
  "cidade_maior_faturamento": "Ourinhos",
  "top_3_atendimentos": [...]
}
```

## 🚀 Como Executar

### Pré-requisitos

- Docker e Docker Compose instalados
- Python 3.7+
- Jupyter Notebook (opcional)

### Passo 1: Iniciar MongoDB

```bash
docker-compose up -d
```

### Passo 2: Executar a Análise

**Opção A: Executar o script Python completo**
```bash
python3 executar_analise.py
```

**Opção B: Executar o Jupyter Notebook**
```bash
jupyter notebook analise_clinica_veterinaria.ipynb
```

## 📁 Arquivos do Projeto

```
exercicio_clinica/
├── dados_clinica.json                      # Dataset com 50 registros
├── docker-compose.yml                       # Configuração do MongoDB
├── README.md                                # Este arquivo
├── executar_analise.py                      # Script Python completo
└── analise_clinica_veterinaria.ipynb       # Notebook Jupyter
```

## 📊 Resultados Principais

### Faturamento por Cidade
- **Ourinhos**: R$ 2.380,00 (26,7%) - Maior faturamento
- **Marília**: R$ 2.275,00 (25,6%)
- **Assis**: R$ 2.220,00 (24,9%)
- **Pompeia**: R$ 2.020,00 (22,7%)

### Faturamento por Serviço
- **Cirurgia**: R$ 3.370,00 (37,9%) - Serviço mais lucrativo
- **Consulta**: R$ 2.655,00 (29,9%)
- **Exame**: R$ 1.505,00 (16,9%)
- **Vacinação**: R$ 830,00 (9,3%)
- **Banho**: R$ 535,00 (6,0%)

### Métricas Gerais
- **Total de Atendimentos**: 50
- **Faturamento Total**: R$ 8.895,00
- **Ticket Médio**: R$ 177,90
- **Maior Atendimento**: R$ 900,00 (Cirurgia - Ourinhos)

### Ticket Médio por Cidade
- **Marília**: R$ 189,58 (maior)
- **Ourinhos**: R$ 183,08
- **Assis**: R$ 170,77
- **Pompeia**: R$ 168,33 (menor)

## 🔍 Queries MongoDB Utilizadas

### Consultar valores entre 90 e 200
```python
collection.find({'valor': {'$gte': 90, '$lte': 200}})
```

### Agrupar por cidade
```python
collection.aggregate([
    {'$group': {'_id': '$cidade', 'total': {'$sum': 1}}},
    {'$sort': {'total': -1}}
])
```

### Agrupar por serviço com faturamento
```python
collection.aggregate([
    {'$group': {
        '_id': '$servico',
        'quantidade': {'$sum': 1},
        'valor_total': {'$sum': '$valor'}
    }}
])
```

## 📚 Tecnologias Utilizadas

- **MongoDB**: Banco de dados NoSQL
- **PyMongo**: Driver Python para MongoDB
- **Pandas**: Análise e manipulação de dados
- **Matplotlib/Seaborn**: Visualização de dados
- **Jupyter Notebook**: Ambiente interativo

## 🎓 Conceitos Praticados

- Operações CRUD no MongoDB
- Agregação e pipeline em MongoDB
- Conversão de dados JSON para DataFrame
- Análise exploratória de dados (EDA)
- Cálculos de métricas e indicadores
- Visualização de dados
- Geração de relatórios estruturados

## ✨ Pontos de Destaque

✓ Dados limpos (0 valores nulos)
✓ Relatório completo com todos os campos obrigatórios
✓ Salvo com sucesso na coleção 'relatorios' do MongoDB
✓ Análises cruzadas por cidade e serviço
✓ Visualizações incluídas no notebook
✓ Código bem documentado e estruturado

---

**Data de Execução**: 26 de março de 2026
**Status**: ✅ Concluído com sucesso