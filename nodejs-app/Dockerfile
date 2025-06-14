#Stage 1
FROM node:22 AS build-env
WORKDIR /app
COPY package*.json ./
RUN npm ci --omit=dev
COPY . .

# Stage 2
FROM gcr.io/distroless/nodejs22-debian12
WORKDIR /app
COPY --from=build-env /app /app
CMD ["app.js"]
