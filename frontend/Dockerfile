# ---- stage 1: build the React app ----
FROM node:20-alpine AS build
WORKDIR /app
 
COPY package*.json ./
RUN npm install --no-audit --no-fund
 
COPY . .
# skips a lint config error that breaks the build ("jest/globals is unknown")
ENV DISABLE_ESLINT_PLUGIN=true
RUN npm run build
 
# ---- stage 2: serve the static files with nginx ----
FROM nginx:alpine
COPY nginx.conf /etc/nginx/conf.d/default.conf
COPY --from=build /app/build /usr/share/nginx/html
 
EXPOSE 3000
CMD ["nginx", "-g", "daemon off;"]

