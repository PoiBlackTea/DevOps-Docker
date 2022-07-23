# DevOps-Docker

## Jenkins
安裝的plugin
- 建議安裝的
- Docker
- Docker Pipeline
- Environment Injector
- Blue Ocean
- Slack notification

---

## prometheus 
alertmanager rules參考自 https://awesome-prometheus-alerts.grep.to/rules.html
啟動指令
```
cd prometheus
docker-compose --env-file ./.env up -d
```
透過traefik進行轉導讓所有服務統一使用port 80對外。

另外prometheus以及alertmanager使用user/password當作帳密，需更改則使用htpasswd建立後更改docker-compose.yml內traefik.http.middlewares.auth.basicauth.users的參數。

|Service|Subpath|
|---|---|
|prometheus|prometheus|
|blackbox-exporter|blackbox|
|altermanager|altermanager|
|cadvisor|cadvisor|
|grafana|grafana|

目前node-exporter沒有web.route-prefix可以使用因此若需要直接存取必須打開對外port

---

## Sonarqube

sonarqube 使用前須調整以下幾個項目
1. sysctl -w vm.max_map_count=262144
2. sysctl -w fs.file-max=65536
預設帳密 admin/admin 第一次須改密碼

---

## Elaticsearch + Kibana
啟動指令
```
cd elasticsearch
docker-compose --env-file ./.env  --compatibility -f docker-compose.yml -f docker-compose-prod.yml  up -d
```