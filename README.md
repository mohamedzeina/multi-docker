## Description
The application is a multi-container setup designed to calculate Fibonacci numbers. It includes the following images/components:

* Client: A React application served on port 3000. Users can enter an index and click submit to obtain the corresponding Fibonacci number.
* Server: An Express server served on port 5000 that handles incoming requests. It communicates with the worker and manages the storage and retrieval of indices and their Fibonacci results.
* Worker: A service responsible for calculating Fibonacci numbers.
* Nginx: Manages routing of requests within the application.
The entered index is stored in a PostgreSQL database. Both the index and its corresponding Fibonacci result are stored in a Redis HashMap.

This application is production-ready for deployment on AWS. Travis CI is configured to run tests on every push to the master branch of the application's git repository. If the tests pass, Travis CI pushes each image to Docker Hub and then automatically deploys the application to AWS Elastic Beanstalk.

For production, AWS services are used instead of local ones:

* AWS RDS: Hosts the PostgreSQL database   
* AWS Elasticache: Provides the Redis cluster

Note: After submitting an index, refresh the page to see the newly calculated results


## How To Build & Run Development Server Locally
Make sure that you have Docker installed on your local machine   
First, clone the repo to your local machine:
```
git clone https://github.com/mohamedzeina/multi-docker.git
```
Then move into the project's directory:
```
cd multi-docker
```
Then, build and run the project using the following docker-compose command:
```
docker-compose -f docker-compose-dev.yml up --build
```
Then, open http://localhost:3050 with your browser to see the result

