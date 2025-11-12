FROM node:18-alpine
WORKDIR /usr/src/app
COPY package*.json ./
RUN npm ci --only=production
COPY . .
ENV NODE_ENV=production
EXPOSE 5000
HEALTHCHECK --interval=30s --timeout=5s --start-period=5s --retries=3 \
  CMD wget -q --spider http://localhost:5000/ || exit 1
CMD ["node", "server.js"]
