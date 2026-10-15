# Start from an official image that already has Node.js 22
FROM node:22-alpine

# All following commands run inside /app in the container
WORKDIR /app

# Copy only the dependency list first, so Docker can reuse this step when only code changes
COPY package.json package-lock.json ./
RUN npm ci --omit=dev

# Now copy the rest of the backend code
COPY . .

# Folder where uploaded files are saved (a volume is attached here later)
RUN mkdir -p public/uploads

ENV NODE_ENV=production
EXPOSE 5000
CMD ["node", "server.js"]