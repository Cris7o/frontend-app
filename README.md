# Frontend App

Aplicación frontend desarrollada con React + Vite, contenedorizada con Docker y desplegada mediante pipeline CI/CD con GitHub Actions.

## Tecnologías
- React + Vite
- Docker (multi-stage build)
- Nginx (servidor de producción)
- GitHub Actions (CI/CD)

## Estructura del proyecto
frontend-app/
├── .github/workflows/deploy.yml  # Pipeline CI/CD
├── src/                          # Código fuente React
├── Dockerfile                    # Multi-stage build
├── .env                          # Variables de entorno
└── vite.config.js

## Variables de entorno
| Variable | Descripción |
|----------|-------------|
| VITE_API_URL | URL del backend (ej: http://localhost:3000) |

## Cómo ejecutar localmente
```bash
docker build --build-arg VITE_API_URL=http://localhost:3000 -t frontend-app .
docker run -p 80:80 frontend-app
```
Abrir: http://localhost

## Pipeline CI/CD
El pipeline se activa con push a la rama `deploy` y realiza:
1. Build de la imagen Docker
2. Push a Docker Hub (`cris7o/frontend-app:latest`)

## Imagen Docker Hub
docker pull cris7o/frontend-app:latest
