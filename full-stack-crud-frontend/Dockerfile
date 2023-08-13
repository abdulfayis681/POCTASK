# Stage 1
FROM node:14 as build-stage

WORKDIR /full-stack-crud-frontend
COPY package.json .
RUN npm install
COPY . .

ARG REACT_APP_API_BASE_URL
ENV REACT_APP_API_BASE_URL=http://10.52.7.136:3002/api

RUN npm run build


# Stage 2
FROM nginx:1.17.0-alpine

COPY --from=build-stage /full-stack-crud-frontend/build /usr/share/nginx/html
EXPOSE 80

ENTRYPOINT ["nginx", "-g", "daemon off;"]

