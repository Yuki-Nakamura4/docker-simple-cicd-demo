FROM node:18 AS base
CMD [ "bash" ]

# Build
FROM base AS build
COPY . /workspace
ARG REACT_APP_API_SERVER
WORKDIR /workspace
RUN npm ci && npm run test && npm run build

# Hosting in nginx
FROM nginx:1.21 AS production
COPY --from=build /workspace/build /var/www
COPY nginx.conf /etc/nginx/nginx.conf