## ** Here Are Some Docker Commands **

docker run -it ubuntu bash
docker run -it python:3.9

docker run -it enterypoint=bash python:3.9

docker build -t test:pandas .

docker run -it test:pandas

----------------------------------------------------------------
ININTIALIZING PG


winpty docker run -it \
  -e POSTGRES_USER="user" \
  -e POSTGRES_PASSWORD="PWD" \
  -e POSTGRES_DB="ny_taxi" \
  -v {pwd}/ny_taxi_postgres_data:/var/lib/postgresql/data  \
  -p 5433:5432 \
  postgres:13

----------------------------------------------------------------
INITIALIZING PGAdmin

winpty docker run -it \
  -e PGADMIN_DEFAULT_EMAIL="email@domain.com" \
  -e PGADMIN_DEFAULT_PASSWORD="PWD" \
  -p 8080:80 \
  dpage/pgadmin4


----------------------------------------------------------
CREATING A NETWORK BETWEEN THE 2

docker network create pg-network


winpty docker run -it \
  -e POSTGRES_USER="user" \
  -e POSTGRES_PASSWORD="PWD" \
  -e POSTGRES_DB="ny_taxi" \
  -v {pwd}/ny_taxi_postgres_data:/var/lib/postgresql/data  \
  -p 5433:5432 \
  --network=pg-network \
  --name pg-database \
  postgres:13

winpty docker run -it \
  -e PGADMIN_DEFAULT_EMAIL="email@domaim.com" \
  -e PGADMIN_DEFAULT_PASSWORD="PWD" \
  -p 8080:80 \
  --network=pg-network \
  --name pgadmin-2 \
  dpage/pgadmin4

