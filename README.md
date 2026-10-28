# Gesture Remote — sitio web

Página de presentación y política de privacidad de Gesture Remote, una app para Android que convierte
gestos de la mano en teclas para controlar presentaciones y multimedia, procesando todo en el teléfono.

Publicado con GitHub Pages en <https://franbenaglia.github.io/gestureRemoteLanding/>.

| Página | Español | English |
| --- | --- | --- |
| Presentación | `index.html` | `en/index.html` |
| Política de privacidad | `privacy.html` | `en/privacy.html` |
| Demo técnica (sin indexar, sin datos de contacto) | — | `demo/index.html` |

La dirección de la política de privacidad para Google Play es
<https://franbenaglia.github.io/gestureRemoteLanding/privacy.html>.

## Estructura

- `assets/style.css`: estilos de todas las páginas, con tema oscuro y claro.
- `assets/`: iconos, gráfico de funciones comprimido y capturas de pantalla.
- `Gesture-Remote-App-Icon-512x512.png` y `Gesture-Remote-Google-Play-Feature-Graphic-1024x500.png`:
  originales para la ficha de Google Play (el ícono es también el del launcher de la app).
- `.nojekyll`: indica a GitHub Pages que sirva los archivos tal cual.

Es un sitio estático: no usa fuentes externas, cookies ni analíticas. El único script es uno en línea,
en las páginas en español, que muestra la versión en inglés si el idioma principal del navegador no es
español; la elección manual de idioma (`?lang=es` / `?lang=en`) se guarda en `localStorage`.

## Publicar

En GitHub: Settings → Pages → Source «Deploy from a branch», rama `main`, carpeta `/ (root)`.

## Descargas (Releases de este repositorio)

El código de la app está en un repositorio privado, así que los archivos se publican en los
**Releases de este repositorio**, que es público. Los enlaces de la página usan
`releases/latest/download/<archivo>`, así que cada release debe incluir estos nombres exactos:

| Archivo | Contenido |
| --- | --- |
| `GestureRemote.apk` | App Android firmada (release) |
| `gesture-receiver-linux-amd64` | Receptor de escritorio para Linux |
| `gesture-receiver-windows-amd64.exe` | Receptor para Windows (beta) |
| `gesture-receiver-macos-arm64` | Receptor para macOS Apple Silicon (beta) |
| `gesture-receiver-macos-amd64` | Receptor para macOS Intel (beta) |

Compilación del receptor (desde `receiver/` en el repositorio del código):

```bash
GOOS=linux   GOARCH=amd64 go build -o gesture-receiver-linux-amd64       ./cmd/gesture-receiver
GOOS=windows GOARCH=amd64 go build -o gesture-receiver-windows-amd64.exe ./cmd/gesture-receiver
GOOS=darwin  GOARCH=arm64 go build -o gesture-receiver-macos-arm64       ./cmd/gesture-receiver
GOOS=darwin  GOARCH=amd64 go build -o gesture-receiver-macos-amd64       ./cmd/gesture-receiver
```
