# Stage 1: Install dependencies only
FROM node:24-alpine AS deps
WORKDIR /app

# Copy ONLY the package files to cache this layer
COPY package*.json ./

# Install dependencies
RUN npm ci

# Stage 2: copy source + deps, run the build
FROM node:24-alpine AS builder
WORKDIR /app

COPY --from=deps /app/node_modules ./node_modules

# Copy the source code
COPY . .

# Install dependencies
RUN npm run build

# Stage 3: final lean image, copies only the build output over
FROM node:24-alpine AS runner
WORKDIR /app

# Adding a non-root user for security
RUN addgroup --system --gid 1001 nodejs
RUN adduser --system --uid 1001 nextjs

# Copy the production node_modules and build output from the builder stage
COPY --from=builder --chown=nextjs:nodejs /app/public ./public
COPY --from=builder --chown=nextjs:nodejs /app/.next/standalone ./
COPY --from=builder --chown=nextjs:nodejs /app/.next/static ./.next/static

USER nextjs
ENV HOSTNAME="0.0.0.0"
EXPOSE 3000
CMD ["node", "server.js"]