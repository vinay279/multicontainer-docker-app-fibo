FROM node:apline as builder

WORKDIR '/app'

COPY ./package.json ./

RUN npm install

COPY ./ ./ 

RUN npm run build 


FROM nginx 

# expose for nginx port same in default.conf
EXPOSE 3000

COPY ./nginx/default.conf /etc/ngnix/conf.d/default.conf

# this is used to copy build folder which is created by there
# builder to this nginx container /usr/share/nginx/html
COPY --from=builder /app/build /usr/share/nginx/html

