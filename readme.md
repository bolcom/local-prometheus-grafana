# How to run local prometheus + grafana instance
to test / validate your metrics...

## how it is set-up
Prometheus is configured to "scrape" the node-exporter container. This container is not necessary, but illustrates how you can add your own LOCAL Java/Go service to be scraped as well.

## how to start
- first download required files
- Unzip contents
- run `docker-compose up` inside directory.
- then open grafana: http://localhost:3000/.
- log-in with username `foo` and password `bar`.
- There is already a dashboard `test` created with one graph, fetching data out of the local prometheus instance. Wait a few minutes, then the data will arrive.

## exposed services
- prometheus server: http://localhost:9090/ (see targets here: http://localhost:9090/targets)
- grafana: http://localhost:3000/
- node-exporter: http://localhost:9100/metrics

When all containers are started, open grafana and open the "test" dashboard.

## how to add your local running service?
Simple, change the prometheus config file (`prometheus.yml`) and add a new target. Since the whole stack is running in docker containers, you should connect to `host.docker.internal:<<your-port>>`. An example can be found in the config file, just uncomment it.

## More info

See this blogpost: << todo >>
