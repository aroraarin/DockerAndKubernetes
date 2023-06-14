# DOCKER ASSIGNMENT

- A Directed Acyclic Graph (DAG) was created, which represents a workflow or a series of tasks to be executed.
- The schedule_interval for the DAG was set to daily, indicating that the tasks within the DAG will be executed once every day.
- The first task, named "create_table_task," was created. This task utilizes the Python Operator with PostgresHook, a component that interacts with a Postgres database. The task is responsible for creating a table in the database. The connection to the Postgres database is established using the "postgres_conn_id" parameter, which is set to "postgres".
- The second task, named "add_entry_table_task," was created. This task also uses the Python Operator and PostgresHook. Its purpose is to insert values into the table previously created in the database.
- Finally, the dependencies between the tasks were established. This means that the tasks were linked in a specific order to ensure they are executed sequentially. For example, "create_table_task" must be completed before "add_entry_task. These dependencies ensure that the tasks are executed in the desired sequence to achieve the intended workflow.

  <img width="548" alt="Screenshot 2023-06-14 at 1 02 10 PM" src="https://github.com/aroraarin/DockerAndKubernetes/assets/122515163/9d1cb171-e291-4089-9c92-a0d06a1ea823">

- Results in postgres table:
  
  <img width="318" alt="Screenshot 2023-06-13 at 12 29 17 PM" src="https://github.com/aroraarin/DockerAndKubernetes/assets/122515163/125064a8-760c-40d2-aae6-b78e33f25292">
  

# KUBERNETES ASSIGNMENT

- Installed minikube. <br>
  `brew install minikube`<br>
  `minikube start`<br>
  
- Created a postgres-deployment.yaml and made a pod using kubectl. <br>
  `kubectl apply -f postgres-deployment.yaml` <br>
  
- Added dependencies of python and airflow in a postgres image by using the following commands inside the postgres pod.
  `apt-get -y update`<br>
  `apt-get  -y install build-essential zlib1g-dev libncurses5-dev libgdbm-dev libnss3-dev libssl-dev libreadline-dev libffi-dev wget`<br>
  `wget https://www.python.org/ftp/python/3.7.12/Python-3.7.12.tgz`<br>
  `tar -xf Python-3.7.12.tgz`<br>
  `cd /Python-3.7.12`<br>
  `./configure --enable-optimizations`<br>
  `make -j $(nproc)`<br>
  `make altinstall`<br>
  `apt-get install libpq-dev`<br>
  `pip3.7 install "apache-airflow[postgres]==2.5.0" --constraint "https://raw.githubusercontent.com/apache/airflow/constraints-2.5.0/constraints-3.7.txt"`<br>
  `airflow db init` <br>
  `airflow users create -u airflow -p airflow -f arin -l arora -e xyz@gmail.com -r Admin` <br>

- Made a postgres-service.yaml and created a service using <br>
  `kubectl apply -f postgres-service.yaml` <br>
  
- Made a airflow-deployment.yaml and created a deployment using <br>
  `kubectl apply -f airflow-deployment.yaml` <br>
  
- Made a airflow-service.yaml and created a service using <br>
  `kubectl apply -f airflow-service.yaml` <br>
  
- Created a DAG and postgres connection and ran it to get the entries in a postgres table. <br>
  
  <img width="1439" alt="Screenshot 2023-06-14 at 12 50 07 PM" src="https://github.com/aroraarin/DockerAndKubernetes/assets/122515163/c56f8bae-900b-4e1a-ae47-d5c527b62e83">

  <img width="1439" alt="Screenshot 2023-06-14 at 12 50 07 PM" src="https://github.com/aroraarin/DockerAndKubernetes/assets/122515163/d00cc7ef-8e14-454a-98d1-d40b9cd1cd60">
  
- Results in table : <br>
  <img width="379" alt="Screenshot 2023-06-14 at 12 52 26 PM" src="https://github.com/aroraarin/DockerAndKubernetes/assets/122515163/a04f1d52-54f8-4aa2-9955-0a381ab39851">

  
  
