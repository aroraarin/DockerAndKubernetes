# Aayush's review: 

## Docker task: 
- He wrote a Python script to create a DAG consisting of tasks that included table creation and data insertion.
- He successfully established a connection between the database and Airflow. 
- To containerize the application, he created a Docker Compose file that encompassed all the necessary services and initiated the containers.
- Afterward, he triggered the DAG and performed data verification within the PostgreSQL container.

## Kubernetes task: 
- He developed a custom PostgreSQL image specifically tailored for serving as the Airflow database. 
- He incorporated this image into his Minikube environment, a Kubernetes cluster management tool.
- By employing the provided PostgreSQL deployment file (postgres-deployment.yaml), he created a pod and initialized the database within it. 
- In order to enable communication with the pod, he established a service using the postgres-service.yaml file. 
- Additionally, he configured a persistent volume using the volumes.yaml file to mount the DAG directory in Airflow. 
- Another service was created using the airflow-service.yaml file to expose Airflow. 
- Finally, he initiated Airflow, triggered the DAG, and confirmed the data in the PostgreSQL container within his Kubernetes deployment.


# Aswat's review:

## Docker task: 
- He containerized Airflow and its components by creating Docker containers. 
- To ensure the installation of psycopg2 in all the containers, he utilized a Dockerfile. 
- Within the Docker containers, he developed a DAG (Directed Acyclic Graph) that consisted of two tasks: Task 1 involved creating a table to store the execution date, while Task 2 involved inserting data into the table. He successfully extracted the execution date using kwargs.

## Kubernetes task:
- He opted to use the Postgres helm chart from the Bitnami repository. 
- By installing the Postgres container using the helm chart, he was able to set the password as "postgres".
- In the Postgres container, he built Python and installed Airflow, specifically version 2.5.0 with Postgres support. 
- To establish the Postgres container as Airflow's database, he initialized it accordingly. 
- He ensured the connection between Airflow and Postgres by setting the environment variable AIRFLOW__DATABASE__SQL_ALCHEMY_CONN to the Postgres connection string. 
- Within the Postgres container, he initialized Airflow's database using the relevant command.
- For the deployment and service of Airflow, he created an Airflow deployment and service, utilizing the Postgres service.
- By applying the Airflow deployment and service configuration from the airflow.yaml file, he effectively managed Airflow's setup.
- Finally, he added the DAG file to the Airflow scheduler, completing the Kubernetes assignment.
