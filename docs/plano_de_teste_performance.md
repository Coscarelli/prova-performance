# Plano de Teste de Performance - Consulta CEP (ViaCEP)

## Contexto
Aplicação pública para consulta de CEPs no Brasil (ViaCEP). O objetivo é simular o pico
no quinto dia útil do mês, com 1000 requisições/hora no período da manhã, rampa de 30 minutos
até atingir o pico e manter steady state por 60 minutos.

## Cenários
1. **Consulta por CEP** (60% do tráfego)
   - Endpoint: `GET /ws/{CEP}/json/`
   - Volumetria: 600 req/hora
2. **Consulta por Endereço** (40% do tráfego)
   - Endpoint: `GET /ws/{UF}/{CIDADE}/{LOGRADOURO}/json/`
   - Volumetria: 400 req/hora

## Parâmetros do teste
- Ramp-up: **30 minutos**
- Steady state: **60 minutos**
- Think time (aleatório): **100 ms a 1000 ms**
- Pacing total durante steady state: **1000 req/hora**

## Critérios de sucesso (sugestão)
- Taxa de erros < 1%
- Tempo médio de resposta < 500 ms (alvo)
- 90th percentile < 1s

## Dados de teste
- `jmeter/data/ceps.csv` — lista de CEPs
- `jmeter/data/enderecos.csv` — lista de endereços (UF,Cidade,Logradouro)

## Resultados e evidências
- Salve os `.jtl` em `jmeter/results/`
- Gere relatório HTML com `jmeter -g results/summary_report.jtl -o results/html-report`
