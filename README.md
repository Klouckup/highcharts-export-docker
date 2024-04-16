# highcharts-export-docker

This repo contains what is required to build the docker image for the highcharts export server v3 running with puppeteer. It uses the more recent node implementation of the highcharts export server:

https://github.com/highcharts/node-export-server

## Build

```
docker build -t klouckup/highcharts-export-node .
```

## Run

```
docker run -d --name highcharts -p 8889:8080 klouckup/highcharts-export-node
```

The above command will expose the service on port 8889. This can be changed if required.

## Test

Once the server is running here is an example curl command to render a chart:

```
curl -H "Content-Type: application/json" -X POST -d '{"infile":{"title": {"text": "Steep Chart"}, "xAxis": {"categories": ["Jan", "Feb", "Mar"]}, "series": [{"data": [29.9, 71.5, 106.4]}]}}' 127.0.0.1:8889 -o testchart.png
```

By default you can access `https://localhost:8889/` for the graphical user interface to test your charts.
