O notebook principal tem o nome random_forest_v2.ipynb


Além deste notebook, há outro chamado data_preprocessing.ipynb onde é feito o pré-processamento dos csvs um a um


A pasta class_imbalance contém os datasets originais que nos foram dados
As pastas clean_class_imbalance e clean_class_imbalance_small contém os datasets depois do pré-processamento (a small tem a metade dos datasets com menos linhas)


As pastas mla, mla2, mla3 e mla4 têm as implementações da Random Forest: mla-original, mla2:mudança x=2, mla3:mudança x=1, mla4:mudança x=3


Além disso temos vários csvs onde guardamos os resultados das medidas de desempenho:
 - analise_inicial_depth_rf.csv : usa o rf original e testa diferentes valores de max_depth
 - analise_inicial_est_rf.csv : usa o rf original e testa diferentes valores de n_estimators
 - analise_sem_mudanca.csv : usa o rf original mas os valores usam só os valores de hiperparametros finais escolhidos
 - analise_mudanca1x.csv: usa o rf com mudança e com o hiperparametro x=1
 - analise_mudanca2x.csv: usa o rf com mudança e com o hiperparametro x=2
 - analise_mudanca3x.csv: usa o rf com mudança e com o hiperparametro x=3
 - resultados_estatisticos.csv: guarda os valores dos testes estatísticos