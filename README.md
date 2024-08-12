# Exercício Prático Cruzeiro do Sul EAD

## Objetivo

Conteúdo do exercício
Como observaram, essa unidade não possui atividades de autocorreção. É proposta uma atividade mais prática, considerando que vocês já possuem instalada a plataforma Hadoop, bem como o mahout, portanto, vocês poderão fazer os experimentos aqui propostos, onde é disponibilizada uma base de textos da Reuters.

A ideia da atividade é vocês executarem o algoritmo kmeans usando uma das pastas com os textos, e analisar qual o resultado do algoritmo. Observem os clusters gerados, e se de fato os assuntos possuem relação entre si. Caso queiram utilizar outras bases de textos, a sequência de comandos deverá funcionar.

## Segue o exemplo e sequência de comandos utilizada:

Base Reuters

C50train

hadoop fs -copyFromLocal C50/ /

mahout seqdirectory -i /C50/C50train -o /seqreuters -xm sequential

mahout seq2sparse -i /seqreuters -o /train-sparse

mahout kmeans -i /train-sparse/tfidf-vectors/ -c /kmeans-train-clusters -o /train-clusters-final -dm org.apache.mahout.common.distance.EuclideanDistanceMeasure -x 10 -k 10 -ow

mahout clusterdump -d /train-sparse/dictionary.file-0 -dt sequencefile -i /train-clusters-final/clusters-10-final -n 10 -b 100 -o ~/saida_clusters.txt -p /train-clusters-final/clustered-points

## ao final da execusão dos comandos acima terá um arquivo com resultados nome saida_clusters.txt

## Passo a Passo
- Ter instalado o virtual box  em sua maquina
- Fazer o download da maquina arquivo virtual [almalinux_8.ova](https://swatpc.cloud/Almalinux_8.ova)
- Importar o arquivo almalinux_8.ova no seu Virtual Box
- Iniciar Maquina Virtual
- login usuário haddop senha 1234
- execurtar o comando para iniciar o haddop  `./start_hadoop.sh`  e  `./stop_hadoop.sh` para parar o haddop
- agora consegue executar as sequencias de comandos acima
  
