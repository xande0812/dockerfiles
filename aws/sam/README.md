# Usage

```
docker build -t sam .

docker run --rm -it sam:latest --help
docker run --rm -it sam:latest local generate-event apigateway aws-proxy >> hoge.json
```
