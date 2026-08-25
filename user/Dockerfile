FROM node:20.19.5-alpine3.21 AS builder
WORKDIR /opt/server
COPY package*.json .
COPY *.js .
# this may add extra cache memeory
RUN npm install


FROM node:20.19.5-alpine3.21
WORKDIR /opt/server
RUN addgroup -S roboshop && adduser -S roboshop -G robosho && \
    chown -R roboshop:roboshop /opt/server
EXPOSE 8080
LABEL com.project="roboshop" \
      component="user" \
      created_by="Vinayraj"
ENV MONGO="true" \
     REDIS_URL="redis://redis:6379" \
     MONGO_URL="mongodb://mongodb:27017/user"
COPY --from=builder --chown=roboshop /opt/server /opt/server
USER roboshop
CMD ["server.js"]
ENTRYPOINT ["node"]









# FROM node:20
# WORKDIR /opt/server
# EXPOSE 8080
# COPY package*.json .
# COPY *.js .
# RUN npm install
# ENV MONGO="true" \
#     REDIS_URL="redis://redis:6379" \
#     MONGO_URL="mongodb://mongodb:27017/user"
# CMD ["node", "server.js"]