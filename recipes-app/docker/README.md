# Recipes Frontend Docker Image

This image provides a web frontend to manage recipes, implemented with [Angular](https://angular.dev/) and served by [NGINX](https://nginx.org/).

## Ports

| Port | Description             |
|------|-------------------------|
| 8080 | HTTP (NGINX web server) |

## Configuration

The application is configured via environment variables. The entrypoint script
substitutes them into the runtime configuration at container startup.

| Environment Variable | Description                    | Default                  |
|----------------------|--------------------------------|--------------------------|
| `API_BASE_URL`       | URL of the Recipes Backend API | `http://localhost:3000`  |

### Example

```bash
docker run -i --rm \
  -p 4200:8080 \
  -e API_BASE_URL=http://backend:8080 \
  ralfueberfuhr/recipes-frontend:latest
```
