FROM node:18.18.0-alpine3.18 as builder
WORKDIR /app/
COPY . /app/
RUN npm i && npm run build

FROM nginx
RUN rm -rf /usr/share/nginx/html/*
COPY --from=builder /app/dist/grades-app-front ./dist/
RUN npm ci --only=production
ENTRYPOINT [ "npm" ]
CMD [ "run",  "start:prod"]
EXPOSE 3000