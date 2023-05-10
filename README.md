# PasswordGenerator

PasswordGenerator is an application that generates random passwords with a number of characters equal to what the user defined in the input.

<img src="/assets/picture-1.png" width="270" /> <img src="/assets/picture-2.png" width="270" />

The main goal of this code is not the development of the application itself, but to demonstrate how to configure and use Docker in conjunction with Nginx and Github Workflow to perform automation tests and deployment in the AWS cloud.

In other words, these configurations enable the CI/CD process with Github Actions.

## Main Technologies
### Back-end
- Node.js
- Express
- Typescript
- PostgreSQL
- Prisma ORM
- Jest

### Front-end
- React.js
- Vite

### DevOps
- Docker
- Nginx
- Github Actions
- AWS Cloud

## How to use the app
Copy and paste the link below into your browser
```bash
http://ec2-18-207-121-52.compute-1.amazonaws.com/
```

## How to run Docker containers on your local machine
1. Make sure you have [Docker](https://www.docker.com/) installed on your machine.
2. Clone this repository
```bash
git clone https://github.com/lucasdosualdo/PasswordGenerator
```
3. Change ports from nginx service in the docker-compose.yml file (on the root) to 8080:80
```bash
nginx:
    container_name: nginx_app
    build: ./nginx
    restart: always
    ports:
      - 8080:80
    volumes:
      - react-volume:/var/www/html
    depends_on:
      - postgres
      - node
      - react
```
4. Create the .env files in the root of the frontend and backend folders according to the .env.example files

Example on back-end .env:
```bash
PORT=5000
DATABASE_URL=postgresql://${POSTGRES_USERNAME}:${POSTGRES_PASSWORD}@postgres:5432/${POSTGRES_DB}
POSTGRES_USERNAME=
POSTGRES_PASSWORD=
POSTGRES_DB=
```
Example on front-end .env:
```bash
VITE_APP_BACKEND_URL=http://localhost:8080/api
```

5. Run
```bash
docker compose up -d
```
6. Finally, access http://localhost:8080 on your favorite browser.


