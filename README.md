# 🚚 Análise Estratégica de Logística: O Impacto do Frete nas Vendas da Olist

## 📊 Visão Geral do Projeto

Este projeto investiga como o custo do frete atua como uma barreira invisível de conversão para a expansão da Olist fora do eixo Sul-Sudeste. Utilizando o dataset público da plataforma com mais de 100 mil pedidos realizados entre 2016 e 2018. A análise parte de uma hipótese central e a testa progressivamente com dados geográficos, volumétricos e por categoria de produto.

---

## 🎯 Tese Central

Regiões com frete proporcionalmente mais caro vendem menos e esse impacto vai além das diferenças de renda e população. Ele se torna especialmente severo em categorias de menor custo, na qual o frete pode representar **mais de 30% do valor do produto**, inviabilizando a conversão no carrinho.

---

## ⚙️ Metodologia

O projeto seguiu um pipeline investigativo estruturado:

1. **Extração e Unificação dos Dados:** quatro tabelas do dataset Olist (pedidos, itens, clientes e produtos) foram unidas via merge para permitir análise cruzada entre frete, região e categoria.
2. **Criação de Métricas Próprias:** foram desenvolvidos indicadores como "pct_frete" (frete como % do preço do produto) e "pct_total_venda" (participação de cada estado/região no volume total de pedidos), que não existiam no dataset original.
3. **Análise Exploratória com Tese:** cada visualização responde a uma pergunta específica dentro da linha investigativa, não apenas descreve variáveis disponíveis.
4. **Recomendação de Negócio:** os achados são convertidos em ação concreta com critérios analíticos explícitos.

---

## 📈 Principais Achados

**Concentração extrema no Sudeste**
São Paulo concentra mais de 42% de todas as vendas da plataforma. O eixo Sudeste como um todo responde por quase 69% dos pedidos.

**O paradoxo Nordeste vs Sul**
O Nordeste tem quase o dobro da população do Sul (54,6M vs 29,9M) e seus clientes compram produtos com ticket médio mais alto. Ainda assim, o Nordeste representa apenas 9,2% das vendas contra 14,3% do Sul. A diferença de renda per capita explica parte do fenômeno, mas não tudo o frete médio do Nordeste (R$ 32,21) é 52% mais caro que o do Sul (R$ 21,24).

**O frete padrão do Norte é mais caro que 75% dos fretes do Sudeste**
A mediana do frete no Norte (R$ 29,10) supera o Q3 do Sudeste (R$ 18,43). O cliente nordestino não enfrenta só um frete mais caro ele enfrenta um frete imprevisivelmente caro, o que gera abandono de carrinho antes mesmo da compra ser concluída.

**O impacto é assimétrico por categoria**
Em Cama/Mesa/Banho e Móveis, o frete representa mais de 33% do valor do produto no Norte. Em Relógios categoria de alto ticket esse impacto cai para ~12%, explicando por que essas categorias vendem relativamente melhor nas regiões distantes.

---

## 💡 Recomendações Estratégicas

**1. Hub logístico no Nordeste**
Bahia e Pernambuco combinam os dois critérios do filtro analítico desenvolvido: frete representando mais de 18% do preço e volume mínimo de 1.000 pedidos. Sua posição geográfica beneficiaria não só o Nordeste, mas aproximaria o escoamento para estados do Norte.

**2. Subsídio seletivo de frete por categoria**
Priorizar subsídio em categorias de ticket baixo (Cama/Mesa/Banho, Móveis, Utilidades Domésticas) nas regiões Norte e Nordeste, onde o impacto do frete é estruturalmente mais alto.

**3. Parcerias com transportadoras regionais**
Reduzir não só o custo médio, mas a variância do frete nessas regiões. O boxplot mostra que o problema é tanto o valor quanto a imprevisibilidade um frete alto mas previsível converte melhor do que um frete incerto.

> ⚠️ Esta recomendação considera apenas os dados de vendas e frete presentes no dataset. Uma decisão real de expansão exigiria avaliar custos operacionais, infraestrutura logística, disponibilidade de transportadoras e localização dos vendedores.

---

## ⚠️ Limitações da Análise

1. **Ausência de dados de checkout:** o dataset contém apenas transações concluídas. Não há acesso a dados de carrinhos abandonados, o que impede mensurar quantos clientes desistiram especificamente por causa do frete.
2. **Fatores socioeconômicos concorrentes:** renda per capita, densidade de sellers e infraestrutura local também influenciam o volume de vendas regional e não foram modelados.
3. **Correlação vs causalidade:** os padrões encontrados indicam forte associação entre frete alto e menor volume de vendas, mas devem ser interpretados como análise exploratória robusta, não como prova causal isolada.

---

## 🛠️ Tecnologias Utilizadas

- **Python 3**
- **Pandas** — manipulação, agregação e criação de métricas
- **Plotly Express / Plotly Graph Objects** — visualizações interativas (choropleth, heatmap, boxplot, scatter com trendline, gráfico dual-axis)
- **Google Colab** — ambiente de desenvolvimento

---

## 📁 Dataset

Dataset público da Olist disponível no
[Kaggle](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce).

Tabelas utilizadas:
- "olist_orders_dataset.csv"
- "olist_order_items_dataset.csv"
- "olist_customers_dataset.csv"
- "olist_products_dataset.csv"
