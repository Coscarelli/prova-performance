# Prova Sicredi - Teste de Performance (ViaCEP API)

## Objetivo
Avaliar o comportamento da API pública ViaCEP sob carga simulando 1000 requisições/hora,
com ramp-up de 30 minutos e steady state de 60 minutos. A carga é dividida entre:
- 60% consultas por CEP
- 40% consultas por endereço

## Estrutura do projeto
```
prova-sicredi-performance/
├── README.md
├── jmeter/
│   ├── Teste_Performance_CEP.jmx
│   ├── data/
│   │   ├── ceps.csv
│   │   └── enderecos.csv
│   └── results/
└── docs/
    └── plano_de_teste_performance.md
```

## Ambiente recomendado
- Apache JMeter **5.6.3**
- Java 11+

## Como executar (linha de comando)
1. Abra um terminal e vá até a pasta `jmeter/`:
   ```bash
   cd jmeter
   ```
2. Execute o JMeter em modo não-GUI (recomendado para testes de carga reais):
   ```bash
   jmeter -n -t Teste_Performance_CEP.jmx -l results/summary_report.jtl
   ```
3. Gere o relatório HTML (opcional):
   ```bash
   jmeter -g results/summary_report.jtl -o results/html-report
   ```

## Observações
- Arquivos de massa estão em `jmeter/data/` (ceps.csv e enderecos.csv).
- O script está configurado para JMeter 5.6.3.
- Ajuste o número de threads/local conforme disponibilidade da sua máquina.

## Autor
Arthur Coscarelli
