## nginx-gunicorn-flask-restful

This repository contains files of a Docker image of
Nginx + Gunicorn + Flask-Restful. 

It was built based on the danriti/nginx-gunicorn-flask image

URL: https://hub.docker.com/r/sivaram002/nginx-gunicorn-flask-restful/

Important parts of the repository:
* The app/views.py contains the main flask-restful api code
* The app/static folder contains the static angularjs index page which utilizes the the api

### Base Docker Image

* [ubuntu:12.04](https://registry.hub.docker.com/_/ubuntu/)


### Docker installation

```
sudo yum install -y docker

sudo service docker start

sudo usermod -a -G docker ec2-user
```

### Building the image from the repository

```
docker build -t flask_restful_app .

docker tag flask_restful_app sivaram002/nginx-gunicorn-flask-restful:angularui

```

### Saving the repository
```
sudo docker save sivaram002/nginx-gunicorn-flask-restful:angularui |gzip > out.tar.gz

```

### Uploading the repository to hub.docker.com
```
docker login --username=sivaram002 --email=siva_ram@outlook.com

docker push sivaram002/nginx-gunicorn-flask-restful:angularui
```
### Running the docker repo on new host
```
docker pull sivaram002/nginx-gunicorn-flask-restful
docker run -d --name my_hello_world3 -p 80:80 sivaram002/nginx-gunicorn-flask-restful:angularui

or
 
curl -L -o out.tar.gz https://www.dropbox.com/s/5h15q3mi4biaql9/nginx-gunicorn-flask-restful.tar.gz?dl=1
docker load < out.tar.gz
docker run -d --name my_hello_world2 -p 80:80 sivaram002/nginx-gunicorn-flask-restful:angularui

```

After few seconds, open `http://<host>` to see the Flask app.
