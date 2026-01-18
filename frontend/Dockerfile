FROM node:18-alpine AS build

WORKDIR /app

# Copy package files
COPY package.json package-lock.json* ./

# Install ALL deps (including devDependencies like vite)
RUN npm install

# Copy source code
COPY . .

# Build Vite app
RUN npm run build


# ---------- Production ----------
FROM nginx:alpine

COPY --from=build /app/dist /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
