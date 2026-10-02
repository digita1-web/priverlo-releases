# priverlo-releases

**Aqui NO hay codigo fuente.** Este repositorio existe solo para **distribuir** Priverlo:

- `docs/` — la **landing** (GitHub Pages): que es, que hace y que **no** hace, permisos, avisos legales y
  las **huellas SHA-256** de la entrega.
- `docs/version.json` — la ultima version publicada, con tamanos, `sha256` y el certificado de firma.
- `docs/legal/` — la licencia (EULA), los avisos de terceros y el aviso etico, para que **viajen con la
  entrega** (ademas de ir **dentro** del APK).
- **Releases** — los binarios firmados (APK para instalar a mano y AAB para una tienda). Los binarios
  **no** estan en el arbol del repositorio: van como adjuntos del release.

## Descargar

- Ultima version: https://github.com/digita1-web/priverlo-releases/releases/latest
- Landing: https://digita1-web.github.io/priverlo-releases/

## Comprobar la descarga

```bash
sha256sum priverlo-1.0.0.apk   # debe coincidir con el sha256 de version.json
```

Priverlo es software propietario. El codigo fuente, el firmware y las pruebas viven en un
repositorio **privado**.
