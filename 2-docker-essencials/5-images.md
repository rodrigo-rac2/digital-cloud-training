## To create the image of a web application in python, for example, we need to:
1. OS - Ubuntu
2. Update `apt` repository
3. Install dependencies using `apt`
4. Install python dependencies with pip
5. Copy source folder to a local folder like `/opt`
6. Run the web server (for example, with the `flask` command)

## Therefore, we need to create a Dockerfile with instructions to do this:
```
Dockerfile

FROM Ubuntu

RUN apt-get update
RUN apt-get install python

RUN pip install flask
RUN pip install flask-mysql

COPY . /opt/source-code

ENTRYPOINT FLASK_APP=/opt/source-code/app.py flask run
```

## To create the image locally on the system

> docker build Dockerfile -t <my-user>/<my-app>

## To push the image to Docker hub

> docker push <my-user>/<my-app>

## To check the history of the Docker image

> docker history <image-name>
