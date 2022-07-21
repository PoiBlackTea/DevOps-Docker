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

## Sonarqube

sonarqube 使用前須調整以下幾個項目
1. sysctl -w vm.max_map_count=262144
2. sysctl -w fs.file-max=65536
預設帳密 admin/admin 第一次須改密碼

## Elaticsearch + Kibana
啟動指令
```
docker-compose --env-file ./.env  --compatibility -f docker-compose.yml -f docker-compose-prod.yml  up -d
```