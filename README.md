1. Install Docker Image

```bash
docker network create jenkins

cd ~/repos/docker-jenkins

docker build -t docker-jenkins:2.387.3-1 .


docker run --name docker-jenkins --restart=on-failure --detach \
  --network jenkins --env DOCKER_HOST=tcp://docker:2376 \
  --env DOCKER_CERT_PATH=/certs/client --env DOCKER_TLS_VERIFY=1 \
  --publish 8080:8080 --publish 50000:50000 \
  --volume jenkins-data:/var/jenkins_home \
  --volume jenkins-docker-certs:/certs/client:ro \
  docker-jenkins:2.387.3-1
```


2. Set-Up Blue Ocean
    1. Get the initial password
        `sudo docker exec docker-jenkins cat /var/jenkins_home/secrets/initialAdminPassword`
    2. Go to your browser localhost:8080
    3. Paste the value
    4. Just Install the Suggested Plugins
    5. Generate Account
        1. username: admin
        2. password: 0408
