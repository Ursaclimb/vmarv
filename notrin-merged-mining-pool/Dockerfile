# Multi-stage build for merged-mining-pool
# Stage 1: Build stage
FROM golang:1.24.1-alpine AS builder

WORKDIR /build

# Install build dependencies
RUN apk add --no-cache git gcc musl-dev

# Copy source code
COPY . .

# Tidy and download dependencies
RUN go mod tidy && go mod download

# Build the application
RUN CGO_ENABLED=1 GOOS=linux go build -a -installsuffix cgo -o merged-mining-pool .

# Stage 2: Runtime stage
FROM alpine:latest

WORKDIR /app

# Install runtime dependencies
RUN apk add --no-cache ca-certificates curl postgresql-client

# Copy binary from builder
COPY --from=builder /build/merged-mining-pool /app/merged-mining-pool

# Copy config example (optional)
COPY config.example.json /app/config.example.json
COPY README.md /app/README.md

# Expose default ports
# API port is typically 8080
EXPOSE 8080
# Stratum ports would be configured via environment
EXPOSE 3333 3334 3335

# Health check
HEALTHCHECK --interval=30s --timeout=10s --start-period=60s --retries=3 \
    CMD curl -f http://localhost:8080/health || exit 1

# Run the application
CMD ["/app/merged-mining-pool"]
