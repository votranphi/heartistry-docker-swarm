# Deploy Heartistry's services using Docker Swarm

![Repo Size](https://img.shields.io/github/repo-size/minhphuc2544/heartistry-docker-swarm)
![Last Commit](https://img.shields.io/github/last-commit/minhphuc2544/heartistry-docker-swarm)
![Open Issues](https://img.shields.io/github/issues/minhphuc2544/heartistry-docker-swarm)
![License](https://img.shields.io/github/license/minhphuc2544/heartistry-docker-swarm)

![Docker](https://img.shields.io/badge/docker-ready-blue?logo=docker)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-v13.5-blue?logo=postgresql)
![MySQL](https://img.shields.io/badge/MySQL-Latest-blue?logo=mysql)
![Redis](https://img.shields.io/badge/Redis-v4.0-lightgrey?logo=redis)
![Prometheus](https://img.shields.io/badge/Prometheus-ready-orange?logo=prometheus)
![Grafana](https://img.shields.io/badge/Grafana-ready-yellow?logo=grafana)
![Tyk](https://img.shields.io/badge/Tyk-API--Gateway-lightblue?logo=tyk)
![Node.js](https://img.shields.io/badge/Node.js-User--Service-brightgreen?logo=node.js)
![Java](https://img.shields.io/badge/Java-Task--Service-red?logo=java)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-Task--Service-green?logo=spring)
![Metrics](https://img.shields.io/badge/Metrics-Prometheus/Grafana-orange?logo=prometheus)

This project provides a comprehensive solution for deploying the Heartistry application using Docker Swarm. Heartistry is a multi-service platform that integrates user and task management, utilizes robust databases (MySQL and PostgreSQL), and includes advanced API management and monitoring tools. This deployment approach leverages Docker Swarm's orchestration capabilities to ensure scalability, high availability, and efficient resource utilization.

# Descriptions

<image src="./deployment_model.svg"></input>
Heartistry's services are deployed using a set of Docker Swarm stacks to handle various components:
- **MySQL Database**: Used for task's data storage.
- **PostgreSQL Database**: Used for user's data storage.
- **User's APIs**: Developed with NestJS, these APIs handle user-related operations such as authentication, user profiles, and other user-centric features.
- **Task's APIs**: Built with Spring Boot, these APIs manage English learning tasks, including vocabulary, sentences, and exercises.
- **Tyk API Gateway**: Serves as the API management layer to proxy requests and secure API interactions.
- **Prometheus + Grafana**: A powerful monitoring stack configured to monitor the health and performance of MySQL, PostgreSQL, Task's APIs, and the Tyk API Gateway.

# Technologies
1. **React**: Builds the user interface of the web app.
2. **Vite**: Bundles and optimizes frontend assets for fast development.
3. **Tyk API Gateway**: Routes, authenticates, and manages API requests.
4. **NestJS**: Implements the Auth/User Service for authentication and user management.
5. **Spring Boot**: Manages the Task Service for English learning tasks.
6. **PostgreSQL**: Stores user-related data for the Auth/User Service.
7. **MySQL**: Stores task-related data for the Task Service.
8. **Prometheus**: Collects and stores metrics for backend services monitoring.
9. **Grafana**: Visualizes metrics from Prometheus in a dashboard.
10. **Docker**: Containers backend services and databases for consistent deployment.  

# How to Install and Run the Project
## Project's structure explaination
```bash
heartistry-docker-swarm/
├───db_exporter        # move analytics generated by 2 databases to Prometheus
├───k6                 # stores Javascript file to call APIs for testing
├───monitoring         # stores Grafana and Prometheus configuration
├───scripts            # stores prerequisites bash script
├───task-service       # Spring Boot project for task's APIs
├───tyk-api-gateway    # proxy API gateway
├───tyk-pump           # move analytics generated by Tyk to Prometheus
│───user-service       # NestJS project for user's APIs
│───.gitmodules        # define reference to 2 backend's projects
│───docker-compose.yml # declares services to be deployed
└───commands.txt       # all the docker commands for deployment
```

## Prerequisites
[Docker](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-20-04) is the only tool needed to deploy this project.

## Installations
```bash
git clone https://github.com/minhphuc2544/heartistry-docker-swarm
```

## Deployments
### Using Docker Compose:
Change the `driver` type of `overlay_network` in `docker_compose.yml` to `bridge` then run this command:
```bash
cd heartistry-docker-swarm
docker compose up -d
```
### Using Docker Swarm:
```bash
# read the commands.txt for more information
```
After successful deployment:
- User's APIs can be called on: [http://<host_ip>:8080/user](http://<host_ip>:8080/user)
- User's APIs Documentation: [http://<host_ip>:8080/user/api](http://<host_ip>:8080/user/api)
- Task's APIs can be called on: [http://<host_ip>:8080/task](http://<host_ip>:8080/task)
- Task's APIs Documentation: [http://<host_ip>:8080/task/swagger-ui.index.html](http://<host_ip>:8080/task/swagger-ui.index.html)
- Grafana Monitoring WebUI: [http://<host_ip>:3000](http://<host_ip>:3000)
- Prometheus Query/Health Check WebUI: [http://<host_ip>:9090](http://<host_ip>:9090)

# License

This project is licensed under the [Apache License 2.0](LICENSE). See the `LICENSE` file for details.

# Credits
Special thanks to our lecturer - [Le Anh Tuan](https://github.com/tuan-devops), University of Information Technology (UIT), Vietnam National University, Ho Chi Minh City (VNU-HCM). The group members are:
- Vo Tran Phi (Student ID: 22521081)  
Github link: [votranphi](https://github.com/votranphi) 
- Le Duong Minh Phuc (Student ID: 22521116)  
Github link: [minhphuc2544](https://github.com/minhphuc2544)