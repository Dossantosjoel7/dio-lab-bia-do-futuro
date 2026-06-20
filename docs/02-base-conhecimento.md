# Base de Conhecimento

## Dados Utilizados

Descreva se usou os arquivos da pasta `data`, por exemplo:

| Arquivo | Formato | Utilização na DenaFin |
|---------|---------|---------------------|
| `historico_atendimento.csv` | CSV | Contextualizar interações anteriores para que o agente tenha "memória" e saiba quais as dúvidas que o cliente já esclareceu.|
| `produtos_financeiros.json` | JSON | Servir como catálogo de mercado. Usado para explicar como funcionam diferentes produtos (ex: CDB, Tesouro Direto) sem fazer recomendações diretas. |
| `faq_educacao_financeira.json` | JSON | Servir como dicionário de conceitos teóricos (ex: Juros Compostos, Inflação, Reserva de Emergência) para sustentar a didática do agente. |
| `transacoes.csv` | CSV | Analisar o padrão de gastos do cliente, calcular totais mensais e categorizar despesas (ex: alimentação, transportes) |

---

## Adaptações nos Dados

> Você modificou ou expandiu os dados mockados? Descreva aqui.

Os ficheiros foram expandidos e adaptados para refletir um ecossistema financeiro realista, em Euros (€), focado num jovem adulto (estudante e trabalhador independente).

1. **Expansão para 4 ficheiros:** O conhecimento foi dividido estrategicamente entre dados comportamentais (`transacoes.csv` e `historico_atendimento.csv`) e dados educativos (`produtos_financeiros.json` e `faq_educacao_financeira.json`).
    
2. **Contexto Realista (`transacoes.csv`):** Inserção de rendimentos de prestação de serviços (ex: estafeta) e despesas reais do dia a dia (ex: supermercado, passes de transporte, propinas de faculdade e custos de formação profissional).
    
3. **Memória de Longo Prazo (`historico_atendimento.csv`):** Adição de uma coluna booleana `resolvido` para permitir que o agente identifique dúvidas anteriores que ficaram pendentes e retome o assunto de forma proativa.
    
4. **Catálogo Nacional (`produtos_financeiros.json`):** Adaptação dos produtos de investimento para a realidade europeia (ex: Certificados de Aforro, PPRs), formatados com "aporte mínimo" e "indicado para" em vez de meras taxas de juro.
    
5. **Separação Didática (`faq_educacao_financeira.json`):** Criação de um ficheiro puramente teórico, onde cada conceito financeiro possui obrigatoriamente um `exemplo_pratico` para forçar a IA a agir como professora.

---

## Estratégia de Integração

### Como os dados são carregados?

Os dados são carregados diretamente para a memória no arranque da aplicação web **Streamlit**.

- Utiliza-se a biblioteca `pandas` para ler, limpar e formatar os dados tabulares dos ficheiros `transacoes.csv` e `historico_atendimento.csv`.
    
- Utiliza-se a biblioteca nativa `json` do Python para carregar o motor de pesquisa (RAG) com os ficheiros `produtos_financeiros.json` e `faq_educacao_financeira.json`.

### Como os dados são usados no prompt?
> Os dados vão no system prompt? São consultados dinamicamente?

[Sua descrição aqui]

---

## Exemplo de Contexto Montado

> Mostre um exemplo de como os dados são formatados para o agente.

```
Dados do Cliente:
- Nome: João Silva
- Perfil: Moderado
- Saldo disponível: R$ 5.000

Últimas transações:
- 01/11: Supermercado - R$ 450
- 03/11: Streaming - R$ 55
...
```
