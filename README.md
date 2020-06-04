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

- Job1 : Pull the Github repo automatically when some developers push repo to Github.
![Screenshot (27)](https://user-images.githubusercontent.com/44314055/83646592-78b38400-a5d1-11ea-97b2-2b6f479824c1.png)

![Screenshot (28)](https://user-images.githubusercontent.com/44314055/83646727-abf61300-a5d1-11ea-95d2-ec9c49854dc1.png)

![Screenshot (29)](https://user-images.githubusercontent.com/44314055/83646763-bd3f1f80-a5d1-11ea-8582-245860c4840f.png)

- OR 

![Screenshot (30)](https://user-images.githubusercontent.com/44314055/83646961-f5466280-a5d1-11ea-8cba-db6e59c10ebc.png)

![Screenshot (31)](https://user-images.githubusercontent.com/44314055/83647014-0a22f600-a5d2-11ea-85a8-91dd59646bf8.png)

![Screenshot (32)](https://user-images.githubusercontent.com/44314055/83648334-89fd9000-a5d3-11ea-812b-34f58eb7eb89.png)

- And My Job-1 Success. 

![Screenshot (38)](https://user-images.githubusercontent.com/44314055/83801725-43895d80-a6c7-11ea-9aee-cc7d1508cd92.png)

