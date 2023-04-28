# Project-3: Give Your Application Auto-Deploy Superpowers

Design and Build CI/CD Pipelines that Support Continuous Delivery Processes.

## Pipeline Diagram
![the design of the pipeline.](https://github.com/AhmedMattar21/ITI-Final-Project-CICD/blob/master/udapeople-pipeline.png)

## Project Setup

#### 1.Create and download a new key pair in AWS.
>Update key pair name in the cloudformation template [backend.yml]



#### 2.Create IAM user for programmatic access only and copy the access key id and secret access key.
>You'll need these credentials to add to CircleCI configuration.



#### 3.Add a PostgreSQL database in RDS that has public accessibility.


#### 4.Setup CloudFront Distribution
  - Choose a random string, such as kk1j287dhjppmz437
  - Create a public S3 bucket with a name that combines "udapeople" and the random string, such as udapeople-kk1j287dhjppmz437.
  - Manually run .circleci/files/cloudfront.yml template file locally, and use bucket name for the Workflow ID parameter.
  ```
  $ cd .circleci/files 
  $ aws cloudformation deploy \
  --template-file cloudfront.yml \
  --stack-name InitialStack\
  --parameter-overrides WorkflowID=udapeople-kk1j287dhjppmz437
  ```
  > Once the initial stack is created, subsequent executions of the cloudfront.yml template will modify the same CloudFront distribution to make the blue-to-green switch without fail.



#### 5.Setup - CircleCI

  - Add SSH Key pair from EC2 to the CircleCI Project Settings > SSH Keys >Additional SSH Keys.
  > To get the actual key pair, you'll need to open the pem file in a text editor and copy the contents. Then you can paste them into Circle CI.
  - Add the following environment variables to your Circle CI project by navigating to {project name} > Settings > Environment Variables.
    
    ```
    AWS_ACCESS_KEY_ID=(from IAM user with programmatic access)
    AWS_SECRET_ACCESS_KEY= (from IAM user with programmatic access)
    AWS_DEFAULT_REGION=(your default region in aws)
    TYPEORM_CONNECTION=postgres
    TYPEORM_MIGRATIONS_DIR=./src/migrations
    TYPEORM_ENTITIES=./src/modules/domain/**/*.entity.ts
    TYPEORM_MIGRATIONS=./src/migrations/*.ts
    TYPEORM_HOST={your postgres database hostname in RDS}
    TYPEORM_PORT=5432 (or the port from RDS if it’s different)
    TYPEORM_USERNAME={your postgres database username in RDS}
    TYPEORM_PASSWORD={your postgres database password in RDS}
    TYPEORM_DATABASE=postgres {or your postgres database name in RDS}
    ```
    
 ## 🔥 Now our pipeline is ready to go!! 🚀
 ### we successfully reduced cost, time, and effort and increased revenue using DevOps culture with continuous delivery and faster time to clients.
![the design of the pipeline.](https://github.com/AhmedMattar21/ITI-Final-Project-CICD/blob/master/success.png)
#### To run the App using docker
```
$ cd util
$ docker compose up
```


### Built With -

- [Circle CI](www.circleci.com) - Cloud-based CI/CD service
- [Amazon AWS](https://aws.amazon.com/) - Cloud services
- [AWS CLI](https://aws.amazon.com/cli/) - Command-line tool for AWS
- [CloudFormation](https://aws.amazon.com/cloudformation/) - Infrastrcuture as code
- [Ansible](https://www.ansible.com/) - Configuration management tool
- [Prometheus](https://prometheus.io/) - Monitoring tool

