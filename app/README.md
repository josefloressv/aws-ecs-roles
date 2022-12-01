# DevOps Simple NodeJS app

How to build & run the app:

```sh
npm install
npm start # node app.js

#with variables
export USER_NAME=Juan
npm start 
```

How to create & run a Docker image:

```sh
# MacOS: the architecture generated is linux/arm64
docker build -t josefloressv/nodeapp:latest --build-arg .

# MacOS: change the architecture generated to linux/amd64
docker build --platform=linux/amd64 -t josefloressv/nodeapp:latest .

# With variables
export USER_NAME=Juan
docker build -t josefloressv/nodeapp:latest --build-arg USER_NAME=Juan .

# run
docker run --name=node01 -itd -p 3000:3000 josefloressv/nodeapp:latest

# run with variables
docker run --name=node01 -itd -e USER_NAME=Juan -p 3000:3000 josefloressv/nodeapp:latest

export USER_NAME=Luis
docker run --name=node01 -e USER_NAME -itd -p 3000:3000 josefloressv/nodeapp:latest

# .. and test
http://localhost:80
```

Tag & push to Docker Registry:
```sh
#Docker Hub
docker login
docker tag josefloressv/nodeapp:latest josefloressv/nodeapp:v1.0
docker push josefloressv/nodeapp:v1.0

#AWS ECR
docker build -t app01-dev .
docker login --username AWS --password $(aws ecr get-login-password --region us-east-1) [AWS_ACCOUNT_NUMBER].dkr.ecr.[AWS_REGION].amazonaws.com
docker tag josefloressv/nodeapp:latest [AWS_ACCOUNT_NUMBER].dkr.ecr.[AWS_REGION].amazonaws.com/nodeapp:latest
docker push [AWS_ACCOUNT_NUMBER].dkr.ecr.[AWS_REGION].amazonaws.com/nodeapp:latest
```

...
