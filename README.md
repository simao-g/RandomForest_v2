# Random Forest com Heurística nas Folhas para Melhor Detecção de Classes Minoritárias

Este projeto apresenta uma modificação no comportamento padrão do algoritmo Random Forest com foco na melhoria da deteção de classes minoritárias em conjuntos de dados desbalanceados. Em cenários onde a classe dominante representa a grande maioria das observações, os modelos tradicionais tendem a favorecer essa classe, resultando numa baixa capacidade de identificar padrões relevantes associados à classe menos representada.

## Motivação

Modelos baseados em árvores de decisão como o Random Forest utilizam, normalmente, uma regra simples nos nós folha: a classe prevista é a classe maioritária entre os exemplos nessas folhas. Embora eficaz na maioria dos cenários, esta abordagem introduz um bias contra a classe minoritária, reduzindo drasticamente métricas como recall e F1-score para essa classe.

A proposta deste trabalho surge da necessidade de tornar o algoritmo mais sensível a padrões locais fortes associados à classe minoritária, sem recorrer a técnicas externas como oversampling, undersampling ou alteração de pesos durante o treino.

## Alteração Proposta

A modificação introduzida consiste em alterar a regra de decisão dos nós folha. Em vez de prever sempre a classe maioritária, um nó folha passa a prever a classe minoritária quando se verifica a seguinte condição:

> A frequência da classe minoritária na folha é superior à sua frequência global no subconjunto de dados utilizado para treinar a árvore.

Assim, evita-se classificar como minoritária por mero ruído estatístico, mas permite-se capturar padrões locais significativos que seriam ignorados pelo método tradicional.

## Estrutura

O notebook principal tem o nome random_forest_v2.ipynb


Além deste notebook, há outro chamado data_preprocessing.ipynb onde é feito o pré-processamento dos csvs um a um.


A pasta data/class_imbalance contém os datasets originais que nos foram dados.
As pastas data/clean_class_imbalance e data/clean_class_imbalance_small contém os datasets depois do pré-processamento (a small tem a metade dos datasets com menos linhas).


As pastas algorithms/mla, algorithms/mla2, algorithms/mla3 e algorithms/mla4 têm as implementações da Random Forest: mla-original, mla2:mudança x=2, mla3:mudança x=1, mla4:mudança x=3. Isto foi feito em diferentes pastas em vez de através da adição da nossa mudança como parâmetro para 'conservar' o 'uso normal' do algoritmo.


Além disso temos um pasta chamada results que contém csvs onde guardamos os resultados das medidas de desempenho:
 - analise_inicial_depth_rf.csv : usa o rf original e testa diferentes valores de max_depth
 - analise_inicial_est_rf.csv : usa o rf original e testa diferentes valores de n_estimators
 - analise_sem_mudanca.csv : usa o rf original mas os valores usam só os valores de hiperparametros finais escolhidos
 - analise_mudanca1x.csv: usa o rf com mudança e com o hiperparametro x=1
 - analise_mudanca2x.csv: usa o rf com mudança e com o hiperparametro x=2
 - analise_mudanca3x.csv: usa o rf com mudança e com o hiperparametro x=3
 - resultados_estatisticos.csv: guarda os valores dos testes estatísticos