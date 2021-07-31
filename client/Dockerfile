FROM node:16-alpine

WORKDIR /app

COPY package.json yarn.lock ./

RUN yarn install --frozen-lockfile

COPY . ./

RUN yarn build


FROM nginx

COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=0 /app/build /usr/share/nginx/html

EXPOSE 3000