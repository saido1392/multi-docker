# Build phase
FROM node:16-alpine AS builder
WORKDIR '/app'
COPY package.json .
RUN npm install
COPY . .
RUN npm run build
# /app/build will contain all needed output

# Run phase
FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html
# dont need to put provide cmd instruction for primary command as starting nginx is already the primary command of base nginx