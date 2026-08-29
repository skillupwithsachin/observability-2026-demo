Your Machine
│
├── Python App
│     └── :8080
│
├── Prometheus Container
│     └── :9090
│
└── Grafana Container
      └── :3000

Commands Used:

**Build Application Image:**
docker build -t observability-demo:1.0 .
docker run -d --name observability-demo   -p 8080:8080   observability-1:demo

**Check Metrics of Application:**
http://localhost:8080/metrics

**Configure Prometheus to scrap metrics: **
docker pull prom/prometheus
docker images | grep prometheus
docker run -d --name prometheus -p 9090:9090 --mount type=bind,source="${PWD}\prometheus.yml",target=/etc/prometheus/prometheus.yml prom/prometheus
http://localhost:9090

<img width="717" height="342" alt="image" src="https://github.com/user-attachments/assets/a90ab070-93c8-4961-ae7c-96b08e0373e1" />


**Pull Grafana Image: **
docker pull grafana/grafana
docker run -d --name grafana -p 3000:3000 grafana/grafana
http://localhost:3000
Username: admin
Password: admin

Prometheus Server URL: http://host.docker.internal:9090

Note: Create connection --> datasource in grafana.


