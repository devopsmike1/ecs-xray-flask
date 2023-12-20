# run xray locally
```
docker build -t xray-daemon .
```

# run container 
```
docker run \
       --attach STDOUT \
      -v ~/.aws/:/root/.aws/:ro \
      -e AWS_REGION=us-east-1 \
      --network xray \
      --name xray-daemon \
      -p 2000:2000/udp \
      xray-daemon -o
```