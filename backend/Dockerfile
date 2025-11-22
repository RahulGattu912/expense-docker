# FROM node:20
#### Using alpine version for smaller image size
#### Intermediate container 1 (IC1)
FROM node:20.18.3-alpine3.21
#### Create a non-root user to run the application
#### On top of IC1 instruction 2 is executed and creates Intermediate container 2 (IC2). IC1 is discarded.
# RUN addgroup -S expense && adduser -S expense -G expense

#### Create application directory
#### On top of IC2 instruction 3 is executed and creates the final container. IC2 is discarded.
# RUN mkdir /opt/backend

#### Give ownership of the application directory to the non-root user
# RUN chown -R expense:expense /opt/backend

#### instead of creating multiple intermediate containers we can chain the commands using &&
# RUN addgroup -S expense && adduser -S expense -G expense
# RUN mkdir /opt/backend
# RUN chown -R expense:expense /opt/backend
# && \ is used to chain commands in a single RUN instruction
###########################################################################################
RUN addgroup -S expense && adduser -S expense -G expense && \
    mkdir /opt/backend && \
    chown -R expense:expense /opt/backend
WORKDIR /opt/backend
ENV DB_HOST="mysql"
#### when we use the host network mode in docker compose we can use localhost to connect mysql
#### ENV DB_HOST="localhost"
#### using host is not recommended for production use cases
USER expense
COPY package.json .
COPY *.js .
RUN npm install
CMD ["node", "index.js"]