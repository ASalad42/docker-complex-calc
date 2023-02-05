FROM node:16-alpine as builder 

WORKDIR '/app'

COPY ./package.json ./

RUN npm install 

COPY . .

RUN npm run build 
# creates default build dir

FROM nginx 
EXPOSE 3000 
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf 
COPY --from=builder /app/build /usr/share/nginx/html


# production dockerfile does not let me run any tests 