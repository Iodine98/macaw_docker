# Dockerfile
FROM node:latest

RUN mkdir /usr/searchx-backend \
    && git clone --branch visual-progress-bar https://github.com/roynirmal/searchx-back-scaffolding.git \
    && cd searchx-backend && npm install # && cp .env.example .env

WORKDIR searchx-backend

CMD ["npm", "run", "start" ]
