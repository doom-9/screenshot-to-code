# NodeJS Version 16
FROM node:18-slim AS builder

# Copy Dir
COPY . ./app

# Work to Dir
WORKDIR /app

# Install Node Package
RUN yarn install --frozen-lockfile && \
    yarn run build

FROM pierrezemb/gostatic

EXPOSE 8043

COPY --from=builder /app/dist /srv/http/

CMD ["-enable-logging","-fallback","index.html"]
