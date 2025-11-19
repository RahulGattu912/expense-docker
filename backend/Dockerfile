# FROM node:20
# Using alpine version for smaller image size
FROM node:20.18.3-alpine3.21
WORKDIR /opt/backend
COPY package.json .
COPY *.js .
RUN npm install
ENV DB_HOST="mysql"
# when we use the host network mode in docker compose we can use localhost to connect mysql
# ENV DB_HOST="localhost"
# using host is not recommended for production use cases
CMD ["node", "index.js"]