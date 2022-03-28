# Docker_Assignment
# Steps

1. Create the aws account
![image](https://user-images.githubusercontent.com/37560890/160313424-7210f1de-36f5-42d3-8362-32e1cb2c7778.png)

2. Create the ec2 intance
      ```- sudo yum update -y
      - sudo amazon-linux-extras install docker
      - sudo yum install docker
      - sudo service docker start
      - sudo usermod -a -G docker ec2-user
      - docker info
      - docker pull postgres
      ```
3. Setup Postgres in a docker container and import any dataset of your liking into it

- https://www.kaggle.com/c/titanic/data Dataset
- Create setup.sql file
```     // Dockerfile
         FROM postgres:alpine
        - COPY *.sql /docker-entrypoint-initdb.d/
        - ADD setup.sql /docker-entrypoint-initdb.d
        - RUN chmod a+r /docker-entrypoint-initdb.d/*
        - EXPOSE 6666 
   ```
 4. Build docker image
        ```docker build -t repo/mypostgres:2 .```
        
 5. Import CSV into database
    ``` docker exec -it mydb psql -U postgres -d post```
    
6. Setup Jupyter in another docker container
    ``` docker run -p 10000:8888 jupyter/scipy-notebook:b418b67c225b```
    
       
