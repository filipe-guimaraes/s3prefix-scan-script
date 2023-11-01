# Como utilizar o comando

01. Substitua o campo s3://bucket/ pelo seu bucket até o prefixo que você deseja realizar a busca.

# Exemplo:
01. Nome do Bucket: filipealmeida/
02. Prefixo da busca: 2023/10/
03. O comando ficará:

  ~~~ shellscript
start=s3://filipealmeida/2023/10/ && \
for prefix in `aws s3 ls $start | awk '{print $2}'`; do
  echo ">>> $prefix <<<"
  aws s3 ls $start$prefix --recursive --summarize | tail -n2
done
~~~

6. O comando abaixo fará uma busca em todos os prefixos após o caminho informado e exibirá informações de quantidade de objetos naquels prefixos posteriores e o volume total de dados nesses prefixos ;)

# Script Geral
~~~ shellscript
start=s3://bucket/ && \
for prefix in `aws s3 ls $start | awk '{print $2}'`; do
  echo ">>> $prefix <<<"
  aws s3 ls $start$prefix --recursive --summarize | tail -n2
done
~~~
