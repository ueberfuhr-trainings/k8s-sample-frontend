# Single-Stage Build: Setzt voraus, dass 'npm run build' bereits ausgeführt wurde
FROM ghcr.io/nginxinc/nginx-unprivileged:alpine

# Umgebungsvariablen deklarieren
ENV API_BASE_URL=http://localhost:3000
ENV PRODUCTION=true

# Kopiere die bereits gebauten Dateien aus dem lokalen dist Ordner
COPY dist/recipes-app/browser /usr/share/nginx/html

# NGINX Konfiguration und Config-Template kopieren
COPY docker/resources/nginx.conf /etc/nginx/conf.d/default.conf
COPY docker/resources/config.template.json /config.template.json

# Entrypoint Skript kopieren und ausführbar machen
COPY --chmod=755 docker/resources/entrypoint.sh /entrypoint.sh

# Schreibrechte für User 101, damit entrypoint.sh config.json schreiben kann
RUN chmod g+w /usr/share/nginx/html

ENTRYPOINT ["/entrypoint.sh"]
CMD ["nginx", "-g", "daemon off;"]
