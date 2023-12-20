# run otel-collector locally

```
docker run --rm -p 4317:4317 -p 55680:55680 -p 8889:8888 -p 2000:2000 \
      -e AWS_REGION=us-west-2 \
      -e AWS_PROFILE=default \
      -v ~/.aws:/home/aoc/.aws/:ro \
      --net xray \
      --name awscollector public.ecr.aws/aws-observability/aws-otel-collector:latest \
      --config /etc/ecs/ecs-default-config.yaml
````

* with prometheus 


```
docker run --rm -p 4317:4317 -p 55680:55680 -p 8889:8888 -p 2000:2000 \
      -e AWS_REGION=us-west-2 \
      -e AWS_PROFILE=default \
      -v ~/.aws:/home/aoc/.aws/:ro \
      --net xray \
      -e AWS_PROMETHEUS_ENDPOINT=https://aps-workspaces.us-west-2.amazonaws.com/workspaces/ws-74b83a50-4082-4b26-a023-d5160263f29a/api/v1/remote_write \
      -e AWS_PROMETHEUS_SCRAPING_ENDPOINT=flask:5000 \
      -v "${PWD}/otel/ecs-default-config.yaml":/etc/ecs/ecs-default-config.yaml:ro \
      --name awscollector public.ecr.aws/aws-observability/aws-otel-collector:latest \
      --config /etc/ecs/ecs-default-config.yaml
```