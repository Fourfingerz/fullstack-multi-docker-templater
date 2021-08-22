# BASE phase
FROM node:alpine as base

WORKDIR '/app'
COPY ./package.json ./
RUN npm install
COPY . .
RUN npm run build

# RUN phase, on port 3000 instead of 80
FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=base /app/build /usr/share/nginx/html