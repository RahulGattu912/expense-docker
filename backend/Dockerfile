FROM node:20
WORKDIR /opt/backend
COPY package.json .
COPY *.js .
RUN npm install
ENV DB_HOST="mysql"
# when we use the host network mode in docker compose we can use localhost to connect mysql
# ENV DB_HOST="localhost"
# using host is not recommended for production use cases
CMD ["node", "index.js"]