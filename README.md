
# Venom IPTV Panel

Panel web informativo para analizar enlaces IPTV basados en paneles Xtream.

## Funciones

* Conversión automática de enlaces IPTV a `get.php`
* Detección de usuario y contraseña desde URLs IPTV
* Consulta de `player_api.php`
* Información del panel:

  * Estado de la cuenta
  * Fecha de expiración
  * Conexiones activas
  * Conexiones disponibles
  * Categorías LIVE / VOD / SERIES
  * Número de canales disponibles
* Interfaz optimizada para **móvil y escritorio**
* Panel oscuro y ligero (HTML + JS puro)

## Uso

1. Pegar un enlace IPTV en el campo de entrada.

Ejemplo:

```
http://example.com:8080/live/usuario/password/12345.ts
```

2. Pulsar **Generar get.php** o **Obtener información**.

El panel detectará automáticamente:

* usuario
* contraseña
* host del servidor
* estado del panel

## Tecnologías

* HTML
* CSS
* JavaScript
* Axios
* Bootstrap

No requiere instalación ni backend.

## Demo

El panel puede ejecutarse directamente desde el navegador.

## Autor

Proyecto desarrollado por **Venom**.

