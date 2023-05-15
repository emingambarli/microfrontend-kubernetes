FROM node:16
WORKDIR /app
COPY package.json .
RUN yarn install
COPY . .
EXPOSE 3002
CMD [ "yarn", "start" ]