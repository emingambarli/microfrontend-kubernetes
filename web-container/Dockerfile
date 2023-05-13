FROM node:latest

WORKDIR /app
COPY . .
EXPOSE 3000
RUN yarn install
RUN yarn upgrade
RUN yarn build
CMD [ "yarn", "start" ]