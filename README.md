# Innova-lab26
Herramienta de extensión LMS diseñada para la accesibilidad

# Mooodle docker image
[Imagen docker con Moodle + Maria DB preconfiruado](https://hub.docker.com/r/bitnami/moodle)

*Instrucciones para instalar por terminal*
curl -LO https://raw.githubusercontent.com/bitnami/containers/main/bitnami/moodle/docker-compose.yml
docker-compose up

# Para trabajo especifico con LTI
- Proveedores de simuladores de LTI como [ltijs](https://github.com/Cvmcosta/ltijs) permiten probar la herramienta con un usuario real de LTI 1.3 sin necesidad de tener Moodle completamente instalado.

- Moodle incluye un probador de herramientas LTI integrado en Administración del sitio → Complementos una vez que esté en funcionamiento.
