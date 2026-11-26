# Use the official Nginx image based on Alpine 3.24 (slim variant).
FROM nginx:1.31.6-alpine3.24-slim

# Upgrade installed packages to the latest versions available from the configured Alpine repositories.
RUN apk upgrade --no-cache

# Remove the default Nginx server configuration.
RUN rm /etc/nginx/conf.d/default.conf

# Copy our application-specific Nginx configuration into the image.
COPY nginx.conf /etc/nginx/nginx.conf

# Copy the Vite production build output into Nginx's document root.
COPY dist /usr/share/nginx/html

# Give the nginx user ownership of the cache directory.
RUN chown -R nginx:nginx /var/cache/nginx

# Run Nginx as a non-root user.
USER nginx

# Declare the container port used by our Nginx configuration.
EXPOSE 8080

# Set the default command for the inherited Nginx entrypoint.
CMD ["nginx", "-g", "daemon off;"]