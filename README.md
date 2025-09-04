## Relatório de Análise do Teste Técnico IMDB 

# Introdução
Este relatório apresenta uma análise sobre a base de dados cinematográfica do IMDB. 
O objetivo do teste era realizar uma análise exploratória dos dados, responder a perguntas específicas e desenvolver um modelo preditivo para a nota do IMDB de filmes. 

# Análise Exploratória de Dados (EDA) 
A análise exploratória foi realizada utilizando alguns passos da metodologia CRISP-DM, abordando os seguintes aspectos:

→ Entendimento dos dados: 
 • Dados sobre recomendação de filmes do IMDB.

→ Preparação dos dados:
 • Tratamento de valores nulos nas colunas Certificate, Meta_score e Gross 
• Conversão de tipos de dados (Released_Year para int, Runtime para int removendo a string "min") 
• Padronização de textos e remoção de espaços extras. 

→ Análise univariada: 
• Identificação de qual o ano com maior número de lançamentos ( filmes) 
• Análise dos filmes com maiores notas (The Godfather, The Dark Knight, etc.) 
• Distribuição de gêneros de filmes nas últimas duas décadas (Drama, Action e Comedy como os mais frequentes). 

→ Análise bivariada: 
• Correlação entre tempo de duração do filme e faturamento.
• Relação entre gênero do filme e faturamento.
• Relação entre nota no IMDB e faturamento.
 
→ Visualizações: 
• Gráficos de barras para distribuição de gêneros dos filmes.
• Gráficos de dispersão para verificar relação entre variáveis numéricas 
• Análise temporal de lançamentos.

## Respostas às Perguntas Específicas
→ Qual filme recomendaria para uma pessoa desconhecida? 
A abordagem utilizada foi recomendar filmes com notas altas no IMDB e com grande número de votos, uma estratégia para recomendação geral. 
Os filmes recomendados incluem clássicos como "The Shawshank Redemption", "The Godfather" e "The Dark Knight", que são amplamente aclamados pela crítica e pelo público.  

→ Fatores relacionados com alta expectativa de faturamento: A análise identificou os seguintes fatores: 
• Gênero do filme: Filmes de ação, aventura e animação tendem a ter maior faturamento.
 • Ano de lançamento: Filmes mais recentes tendem a ter maior faturamento 
• Classificação etária: Filmes com classificação mais abrangente (PG, PG-) tendem a ter maior público 
• Elenco: A presença de atores famosos está correlacionada com maior faturamento 
• Diretor: Diretores renomados também influenciam positivamente o faturamento.

→ Insights da coluna Overview
A análise da coluna Overview foi executada utilizando técnicas de processamento de linguagem natural.
• Pré-processamento de texto (remoção de stopwords, tokenização, etc.).
• Aplicação de TF-IDF para vetorização.
• Uso de Latent Dirichlet Allocation (LDA) para identificar tópicos.
• Treinamento do modelo Naive Bayes para prever o gênero a partir da sinopse.

Os resultados mostraram que é possível inferir o gênero do filme a partir da sinopse, entretanto com precisão limitada. Isso se deve ao tamanho reduzido do dataset, modelos de ML funcionam melhor com bases mais robustas. 
No Modelo Preditivo para Nota IMDB, foi identificado como um problema de regressão, já que a nota IMDB é uma variável contínua. 

→ Transformações aplicadas 
• Aplicação de log em variáveis enviesadas (Gross, No_of_Votes) 
• Codificação one-hot para variáveis categóricas 
• Normalização de variáveis numéricas 

→ Foram testados diferentes modelos: 
• Regressão Linear .
• Random Forest Regressor
• Gradient Boosting Regressor 
O modelo de Gradient Boosting apresentou o melhor desempenho, com menor erro quadrático médio (RMSE). 

→  As métricas de avaliação escolhidas foram:
 • RMSE (Root Mean Squared Error) 
• R² (Coeficiente de Determinação) 

→ O modelo previu uma nota próxima à real para o filme "The Shawshank Redemption", demonstrando boa capacidade preditiva. 

→ O modelo foi salvo em formato .pkl, permitindo sua reutilização futura sem necessidade de retreinamento. 

O modelo preditivo desenvolvido pode ser uma ferramenta valiosa para o estúdio PProductions na tomada de decisões sobre futuros projetos cinematográficos, permitindo estimar o potencial de recepção crítica de diferentes conceitos de filmes.
