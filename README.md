# NodeApp

docker build -t myjenk .

docker run -d -v /var/run/docker.sock:/var/run/docker.sock \
-v $(which docker):/usr/bin/docker -p 8080:8080 myjenk
