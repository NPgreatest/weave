# Build weave frontend
FROM node:lts-alpine AS builder
WORKDIR /weave
COPY . .
RUN npm install && \
    npm run build

# Setup nginx server for frontend
FROM nginx:stable-alpine
COPY --from=builder /weave/dist/ /usr/share/nginx/html/
RUN rm -f /etc/nginx/conf.d/*
EXPOSE 80
CMD ["nginx", "-g", "daemon off;" ]
