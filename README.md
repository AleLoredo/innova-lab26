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

# LTI
- [Documentacion de LTI](https://www.1edtech.org/standards/lti)

- Proveedores de simuladores de LTI como [ltijs](https://github.com/Cvmcosta/ltijs) permiten probar la herramienta con un usuario real de LTI 1.3 sin necesidad de tener Moodle completamente instalado.

- Moodle incluye un probador de herramientas LTI integrado en Administración del sitio → Complementos una vez que esté en funcionamiento.

### Flujo de LTI + Advantage
Moodle inicia un flujo OAuth 2.0 con la app y esta recibe un JWT firmado con toda la info del usuario (nombre, email, rol, curso, etc.).
La app valida la firma usando la clave pública de Moodle.
Con esto ya sabemos quien es el usuario, qué rol tiene (estudiante, docente, admin) y desde qué curso viene.

Usuario click en Moodle
        │
        ▼
[1] OIDC Login Initiation
    Moodle → POST /lti/login  (tu app)
    Params: iss, login_hint, target_link_uri
        │
        ▼
[2] Authentication Request
    Tu app → redirect a Moodle con:
    response_type=id_token, nonce, state
        │
        ▼
[3] Token Launch
    Moodle → POST /lti/launch  (tu app)
    Body: id_token (JWT firmado)
        │
        ▼
[4] Validación del JWT
    Tu app descarga JWKS de Moodle
    Verifica firma, iss, aud, nonce, exp
        │
        ▼
[5] Sesión creada
    Ya sabés: nombre, email, rol, curso_id


### El formato del |JWT

    {
  "sub": "user-id-unico",
  "email": "alumno@universidad.edu",
  "name": "Juan Pérez",
  "https://purl.imsglobal.org/spec/lti/claim/roles": [
    "http://purl.imsglobal.org/vocab/lis/v2/membership#Learner"
  ],
  "https://purl.imsglobal.org/spec/lti/claim/context": {
    "id": "curso-123",
    "title": "Matemáticas II"
  },
  "https://purl.imsglobal.org/spec/lti/claim/resource_link": {
    "id": "recurso-456"
  }
}
