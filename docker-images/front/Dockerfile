# Dockerfile
FROM node:latest

RUN mkdir /usr/searchx-frontend \
    && git clone --branch visual-progress-bar https://github.com/roynirmal/searchx-front-scaffolding.git \
    && cd searchx-frontend && npm install

WORKDIR searchx-frontend

CMD ["npm", "start"]
