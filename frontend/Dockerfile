FROM node:18-alpine
WORKDIR /usr/src/app

# Install dependencies (use package-lock for deterministic install)
COPY package*.json ./
# only install production deps to keep image small
RUN npm ci --only=production

# copy source
COPY . .

# set environment
ENV NODE_ENV=production
EXPOSE 5000

# Healthcheck (optional)
HEALTHCHECK --interval=30s --timeout=5s --start-period=5s --retries=3 \
  CMD wget -q --spider http://localhost:5000/ || exit 1

# start the app (adjust the start command if different)
CMD ["node", "server.js"]
