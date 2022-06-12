##  prisma-with-db
Prisma, Docker, PostgreSQL, Playground porject

### Set up Prisma / Start from scratch
(Relational databases)[https://www.prisma.io/docs/getting-started/setup-prisma/start-from-scratch/relational-databases-typescript-postgres]

### database setup
```
// Use docker run database
$ docker pull postgres
$ docker run --name postgresql -e POSTGRES_USER=johndoe -e POSTGRES_PASSWORD=randompassword -p 5432:5432 -v $(pwd)/data:/var/lib/postgresql/data -d postgres
$ docker start postgresql
$ docker stop postgresql

// Prisma Studio is a visual editor for the data in your database. 
$ npx prisma studio

// pgadmin4
$ docker pull dpage/pgadmin4:latest
$ docker run --name my-pgadmin -p 8081:80 -e 'PGADMIN_DEFAULT_EMAIL=user@testlocal.com' -e 'PGADMIN_DEFAULT_PASSWORD=randompassword' -d dpage/pgadmin4
$ docker inspect postgresql -f "{{json .NetworkSettings.Networks.bridge.IPAddress}}"

// Create migrations from your Prisma schema, apply them to the database, generate artifacts
$ prisma migrate dev --name ${migration_name}

// Seeding your database, it allows you to consistently re-create the same data in your database and can be used
$ npx prisma db seed
```