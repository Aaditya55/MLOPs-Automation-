# MLOPs - Automation :
MLOPs Task 3

# Project on integration of Machine Learning with Devops.
#### This project is based on the the automation of machine lerning model , when it'll be integrated with docker & jenkins. Bascially to create a machine learning model is not a tough task as we've to run it , or trained it & find the accuracy all these things we can find easily with the automation process. we have to only define the job in jenkins according to the our requirements & use cases.

## Feature of Project
   - Create container image that’s has Python3 and Keras or numpy installed using dockerfile

   - When we launch this image, it should automatically starts train the model in the container.

   - Create a job chain of job1, job2, job3, job4 and job5 using build pipeline plugin in Jenkins

   - Job1 : Pull the Github repo automatically when some developers push repo to Github.

   - Job2 : We've to the build the our own docker image according the our code ( that docker image has been created by me though the Dockerfile inside that we've to write the all the libraries required for that code ).

   - Job3 : We've to launch the container in docker according to our CNN code.

   - Job4 : We,ve to run the CNN code inside our docker & find the Accuracy of the model.

   - Job5 : We,ve to send the notification to the developer if accuracy of the model is more than 80%.
   

## CODE For Dockerfile:

- FROM centos:latest

- RUN yum install python3 -y 
- RUN pip install --upgrade pip 
- RUN pip3 install keras
- RUN pip3 install tensorflow
- RUN pip3 install numpy
- RUN pip3 imnstall pandas
- RUN pip3 install skilearn
- RUN pip3 install scipy
- RUN pip3 imnstall pillow
- RUN pip3 imnstall matplotlib
- RUN pip3 imnstall seaborn

## I start jenkins where i create the chain of job to run the all the processs automatically.

## Job1 : Pull the Github repo automatically when some developers push repo to Github.

![Screenshot (27)](https://user-images.githubusercontent.com/44314055/83646592-78b38400-a5d1-11ea-97b2-2b6f479824c1.png)

![Screenshot (28)](https://user-images.githubusercontent.com/44314055/83646727-abf61300-a5d1-11ea-95d2-ec9c49854dc1.png)

![Screenshot (29)](https://user-images.githubusercontent.com/44314055/83646763-bd3f1f80-a5d1-11ea-8582-245860c4840f.png)

- OR 

![Screenshot (30)](https://user-images.githubusercontent.com/44314055/83646961-f5466280-a5d1-11ea-8cba-db6e59c10ebc.png)

![Screenshot (31)](https://user-images.githubusercontent.com/44314055/83647014-0a22f600-a5d2-11ea-85a8-91dd59646bf8.png)

![Screenshot (32)](https://user-images.githubusercontent.com/44314055/83648334-89fd9000-a5d3-11ea-812b-34f58eb7eb89.png)

- And My Job-1 Success. 

sudo cp -v -r -f * /root

#### Job 1 Success

![Screenshot (38)](https://user-images.githubusercontent.com/44314055/83801725-43895d80-a6c7-11ea-9aee-cc7d1508cd92.png)

## Job2 : 
       This is to check the container required for model training and starting it. We've to the build the docker image . 

 ![Screenshot (39)](https://user-images.githubusercontent.com/44314055/83809592-535b6e80-a6d4-11ea-8169-e85132a0b6ba.png)

 ![Screenshot (54)](https://user-images.githubusercontent.com/44314055/83954558-e37ded00-a867-11ea-802c-dc48bf1850b0.png)


 if sudo docker ps -a | grep tensorenv
 then
 sudo docker rm -f tensorenv
    echo "working"
- elif sudo docker ps -a | grep sklearn
- then
- sudo docker rm -f sklearn
- fi

- if sudo cat /root/mnist.py | grep keras
- then
- sudo docker run -d -i -v /root:/root --name tensorenv tensork 
  -   echo "Tensorflow container is launched"
  -   exit 0
   
- elif sudo cat /root/mnist.py | grep sklearn
- then
- sudo docker run -d -i -v /root:/root --name sklearn  sklearn:v1
  -   echo "sklearn container is launched"
  -   exit 0
- else
- echo "Different Code then ML & DL "
   
- fi

#### Job 2 Success

![Screenshot (52)](https://user-images.githubusercontent.com/44314055/83954581-0c05e700-a868-11ea-97e5-a820866c9b71.png)


## Job3 :
        This job purpose is to run and train the model only.

![Screenshot (41)](https://user-images.githubusercontent.com/44314055/83809642-74bc5a80-a6d4-11ea-8b60-d42de5389293.png)

- sudo cd /root/
- sudo docker exec -w /root tensorenv python3 Chirag-pro-1.py > accr.txt


![Screenshot (55)](https://user-images.githubusercontent.com/44314055/83954606-61da8f00-a868-11ea-9fde-15dbd7410907.png)

#### Job 3 Success

![Screenshot (53)](https://user-images.githubusercontent.com/44314055/83954618-80408a80-a868-11ea-96e1-e8c5a9e527f8.png)


## Job 4 :
        Now this job is very important and owes almost all the automation. Here we are comparing the accuracy stored in a text file to our desired level (in my case it is 85% i.e 0.85). 

![Screenshot (43)](https://user-images.githubusercontent.com/44314055/83812697-966c1080-a6d9-11ea-93f4-a4238e8e9610.png)

- sudo docker cp tensorsenv:/root/accr.txt .
- sudo docker cp tensorsenv:/root/learning_parameters.py .
- echo $(cat accr.txt)
- if [[" $(cat accr.txt) " < " 0.8500 " ]]
- then
   - echo "Model twicking"
   - sudo chmod 0777 /root/parameters.py
   - echo -e "ler_para=ler_para*0.1" >> learning_parameters.py   
   - sudo docker exec -tt -w /root tensorsenv echo -e "ler_para*0.1" >> learning_parameters.py
   - sudo "Model twicked"
   - exit 1
       
- else
     - echo "Model Trained"
     - exit 0
- fi

![Screenshot (58)](https://user-images.githubusercontent.com/44314055/83954889-b717a000-a86a-11ea-96e6-5c50c08304ab.png)

#### Job 4 Success 

![Screenshot (62)](https://user-images.githubusercontent.com/44314055/83969731-351d8a80-a8ef-11ea-9215-e5aa28021d28.png)


