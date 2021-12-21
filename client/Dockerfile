FROM node:16-alpine as x

WORKDIR '/app'

COPY package.json .
RUN npm install
COPY . .

RUN npm run build

FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=x /app/build /usr/share/nginx/html

