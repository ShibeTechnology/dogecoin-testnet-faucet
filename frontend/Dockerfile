FROM node:latest AS builder

# Create app directory
WORKDIR /usr/src/app

# Copy source files
COPY . .

RUN npm install
RUN cp -r src dist
RUN npm run browserify:dist

FROM nginx:1.27

COPY --from=builder /usr/src/app/dist /usr/share/nginx/html/
