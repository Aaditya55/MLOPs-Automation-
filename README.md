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
