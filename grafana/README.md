# grafana

```
docker run  -d -p 3000:3000 --name=grafanaen -v  ~/.aws:/usr/share/grafana/.aws/:ro  -e AWS_SDK_LOAD_CONFIG=true -e GF_AUTH_SIGV4_AUTH_ENABLED=true grafana/grafana-enterprise
```
|