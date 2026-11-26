# Use a Java 21 runtime image based on Ubuntu 24.04 LTS.
FROM eclipse-temurin:21-jre-noble

# Add metadata to identify and describe the container image.
LABEL org.opencontainers.image.title="CWVJ User Management API" \
      org.opencontainers.image.description="Spring Boot backend for the Cloud With VarJosh GitHub Actions Mega Project" \
      org.opencontainers.image.vendor="Cloud With VarJosh"

# Create a dedicated non-root system group and user for running the application.
RUN groupadd --system --gid 10001 appuser \
    && useradd --system \
       --uid 10001 \
       --gid 10001 \
       --no-create-home \
       --shell /usr/sbin/nologin \
       appuser

# Set /app as the working directory inside the container.
WORKDIR /app

# Copy the backend JAR into the image and assign ownership to UID 10001 and GID 10001.
COPY --chown=10001:10001 user-management-api.jar app.jar

# Run the application as the non-root user and group.
USER 10001:10001

# Document the port on which the backend application listens.
EXPOSE 8080

# Start the Spring Boot application when the container launches.
ENTRYPOINT ["java", "-jar", "app.jar"]