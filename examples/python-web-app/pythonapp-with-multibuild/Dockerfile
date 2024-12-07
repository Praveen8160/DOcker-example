# Stage 1: Build Stage
FROM python:3.9-slim as build

WORKDIR /app

# Copy application files and dependencies
COPY requirements.txt /app
COPY devops /app

# Install dependencies into a separate directory to copy later
RUN pip install --upgrade pip && \
    pip install --target=/app/dependencies -r requirements.txt

######################################################
#                 Multi-Stage Build
######################################################
# Stage 2: Distroless Image
FROM gcr.io/distroless/python3

WORKDIR /app

# Copy the application and its dependencies from the build stage
COPY --from=build /app/devops /app/devops
COPY --from=build /app/dependencies /app/dependencies

# Set the Python path to include the dependencies
ENV PYTHONPATH=/app/dependencies

# Entry point for running the application
ENTRYPOINT ["python"]
CMD ["manage.py", "runserver", "0.0.0.0:8000"]

