# 4-Aug-2021
Task:
  1.pull docker postgres
  2.network ubuntu and postgres docker containers
  3.connect to postgres from notebook and create one row in a table
 **pulled docker postgres**
   1.docker pull postgres:alpine
   2.docker images
   3.docker run --name dtbse -e POSTGRES_PASSWORD=password -d -p 5432:5432 postgres:alpine
   4.docker ps
   5.docker exec -it dtbse 
   @@ got error beacause didnt mention bash
   6.docker exec -it dtbse bash
   7.pwd
   8.ls
   9.psql
   @@ doesnt connected
   10.psql --help
   @@ using this got the command
   11.psql -U postgres
   @@ final stage-- got pulled and entered into postgres
   
   **Network ubuntu and postgres
  
1.docker network ls                               
2.docker network create --driver driver_name network_name
  exact command used by mine(docker network create --driver bridge new_network) 
3.docker run -it --network=new_network ubuntu:latest /bin/bash 
4.docker run -it --network=new_network --name hima_postgres -e POSTGRES_PASSWORD=mysecretpassword -d postgres
5.docker inspect new_network
@@ got connected network


**connect to postgres from notebook
  
  1.pip install ipython-sql
  2.pip list
  3.pip install psycopg2
  @@ used this but got error
  4.pip install psycopg2-binary
  @@got installed
  5.pip install sqlalchemy
  6.%load_ext sql
  7.from sqlalchemy import create_engine
  8.%sql dialect+driver://username:password@host:port/database
  @@ got error Connection info needed in SQLAlchemy format, example:
               postgresql://username:password@hostname/dbname
               or an existing connection: dict_keys([])
               invalid literal for int() with base 10: 'port'
               Connection info needed in SQLAlchemy format, example:
               postgresql://username:password@hostname/dbname
               or an existing connection: dict_keys([])
    got errors and stucked
 **refrences
 1. https://gregtczap.com/blog/docker-postgres-ubuntu-localhost/
 2. https://www.geeksforgeeks.org/creating-a-network-in-docker-and-connecting-a-container-to-that-network/#:~:text=%20%20%201%20Step%201%3A%20.%20In,next%20step%20connect%20the%20container%20to...%20More%20
 3. https://www.bing.com/videos/search?view=detail&mid=56AFAB710730DE000BDE56AFAB710730DE000BDE&q=connect
 4. https://www.youtube.com/watch?v=aHbE3pTyG-Q
 5. https://www.youtube.com/watch?v=2PDkXviEMD0
 6. https://shravan-kuchkula.github.io/sql/postgres-jupyter/#step-1-first-make-sure-you-install-homebrew-if-you-dont-already-have-it
 7. https://medium.com/analytics-vidhya/postgresql-integration-with-jupyter-notebook-deb97579a38d
 8. https://blog.panoply.io/connecting-jupyter-notebook-with-postgresql-for-python-data-analysis#:~:text=%20Connecting%20Python%20pandas%20and%20Jupyter%20Notebooks%20to,following%20along%20in%20your%20own%20Jupyter...%20More%20
