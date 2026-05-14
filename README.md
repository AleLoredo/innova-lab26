# Innova-lab26
Herramienta de extensión LMS diseñada para la accesibilidad

# Mooodle docker image
[Imagen docker con Moodle + Maria DB preconfiruado](https://hub.docker.com/r/bitnami/moodle)

## Instalación por terminal

### 1. Descargar el archivo `docker-compose.yml`
```bash
curl -LO https://raw.githubusercontent.com/bitnami/containers/main/bitnami/moodle/docker-compose.yml
```
### 2. Correr el contenedor
```bash
docker-compose up
```
### 2bis. O bienn correr el contenedor modo detach
```bash
docker-compose up -d
```

# Para trabajo especifico con LTI
- Proveedores de simuladores de LTI como [ltijs](https://github.com/Cvmcosta/ltijs) permiten probar la herramienta con un usuario real de LTI 1.3 sin necesidad de tener Moodle completamente instalado.

- Moodle incluye un probador de herramientas LTI integrado en Administración del sitio → Complementos una vez que esté en funcionamiento.
