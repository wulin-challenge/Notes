# SQLServer

## 安装配置
### Docker安装
- [dockerhub网址](https://hub.docker.com/r/exoplatform/sqlserver/)

docker run -d -e SA_PASSWORD=<passord> -e SQLSERVER_DATABASE=<db name> -e SQLSERVER_USER=<user> -e 
SQLSERVER_PASSWORD=<password> -p <local port>:1433 exoplatform/sqlserver:ctp2-1-1

docker run -d -e SA_PASSWORD=ad -e SQLSERVER_DATABASE=mythos -e SQLSERVER_USER=myth -e SQLSERVER_PASSWORD=jiushi -p 1433:1433 mssql