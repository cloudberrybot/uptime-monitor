# uptime-monitor

## Introduction

There are two projects inside the NX monorepo:

`uptime-monitor-engine`: engine that runs the uptime and content requirements checks.
`uptime-monitor-service`: microservice that stores the data generated by the `uptime-monitor-engine`

Run `nx graph` to see a diagram of the dependencies of the projects.

## Tooling

Nodejs LTS
Docker
Playwright
Nx

## Environment variables

### Database

Create a .env file inside /database and set a value for `DB_PASSWORD`. We recommend not to update the DB_NAME value, if you do make sure to update the docker-compose.yml file and the Prisma .env file.

```shell
DB_USER=admin
DB_PASSWORD=
DB_PORT=5432
DB_NAME=uptime
```

### ORM (Prisma)

Prisma is the ORM used to communicate with the database.

Create a .env file inside /prisma and set a DATABASE_URL value. Replace <DB_PASSWORD> with the password you set on the previous step.

```shell
DATABASE_URL=postgresql://admin:<DB_PASSWORD>@localhost:5432/uptime?schema=monitor
```

## Run the solution

Following steps should run in different terminal windows.

### Database

`uptime-monitor-service` logs the check events in the `uptime` mongo db collection.

Open a new terminal or console and run the following comands to spin up the database. 

```terminal
cd database
docker compose up
```

### Run the microservice

```shell
npx nx server uptime-monitor-service
```

### Run the engine

```shell
npx nx server uptime-monitor-engine

```
