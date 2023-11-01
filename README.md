~~~ shellscript
start=s3://bucket/ && \
for prefix in `aws s3 ls $start | awk '{print $2}'`; do
  echo ">>> $prefix <<<"
  aws s3 ls $start$prefix --recursive --summarize | tail -n2
done
~~~
