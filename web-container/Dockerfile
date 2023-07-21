FROM node:latest
WORKDIR /app
ENV REACT_APP_HEADER_HOST=http://10.104.218.63:3001
ENV REACT_APP_BLOGS_HOST=http://10.103.57.36:3002
COPY package.json .
RUN yarn install
COPY . .
EXPOSE 3000
CMD [ "yarn", "start" ]