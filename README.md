# NestJs API

A NestJS-based server-side application.

## Project Setup

Install dependencies:

```bash
yarn install
```

## Environment Variables

Before running the project, create a .env file in the root directory:

```bash
cp .env.example .env
```

Then edit .env and set your actual secrets and database info:

```bash
DATABASE_URL="postgresql://<POSTGRES_USER>:<POSTGRES_PASSWORD>@localhost:5434/<POSTGRES_DB>?schema=public"
JWT_SECRET="<your-secret>"
```

## Docker Compose

Update your docker-compose.yml file with the database credentials you set in .env:

```yaml
environment:
  POSTGRES_USER: ${POSTGRES_USER}
  POSTGRES_PASSWORD: ${POSTGRES_PASSWORD}
  POSTGRES_DB: ${POSTGRES_DB}
```

## Prerequisites

- Docker and Docker Compose installed
- Prisma CLI installed or accessible via npm scripts

## Starting the Database

Start the database container:

```bash
yarn db:dev:up
```

## Applying Migrations

Apply Prisma migrations after the database container is running:

```bash
yarn prisma:dev:deploy
```

## Restarting the Database and Applying Migrations (useful)

Reset the database container and apply migrations:

```bash
yarn db:dev:restart
```

## Running the Application

### Development

```bash
yarn start:dev
```

## Testing the API

### Sign up a user:

```bash
curl -X POST http://localhost:3000/auth/signup \
-H "Content-Type: application/json" \
-d '{"email":"test@shopo.com", "password":"123456"}'
```

### Sign in a user:

```bash
curl -X POST http://localhost:3000/auth/signin \
-H "Content-Type: application/json" \
-d '{"email":"test@shopo.com", "password":"123456"}'
```
