# THIRD_PARTY_NOTICES — PhantomAudit

Avisos de componentes de terceros. Forma parte integrante de [`LICENSE`](./LICENSE).
Lista **solo** las dependencias que el proyecto va a usar. Todavía no hay código: este
documento se actualiza al aprobar cada dependencia (ver `docs/HARNESS.md` → POLÍTICA DE
LICENCIAS) y debe reproducir los avisos exigidos por cada licencia en la distribución binaria.

| Nombre | Versión | Licencia | URL | Texto de copyright / notas |
|---|---|---|---|---|
| PlatformIO Core | 6.2.0 (instalado con pipx) | Apache-2.0 | https://github.com/platformio/platformio-core | `LICENSE` contiene el texto Apache-2.0 sin línea de copyright propia (no existe `NOTICE`). Metadato PyPI: "Apache Software License". Es herramienta de **build**: no se distribuye dentro del binario |
| PlatformIO platform `espressif32` | **7.1.3** (pin aplicado en `firmware/platformio.ini`) | Apache-2.0 | https://github.com/platformio/platform-espressif32 | Fija el stack: `framework-arduinoespressif32`, `toolchain-xtensa-esp32 8.4.0+2021r2-patch5`, `tool-esptoolpy 2.41100.260830 (4.11.0)`, `tool-scons 4.41101.0`. Build-time |
| ESP-IDF | **4.4.7** (incluido en el core instalado) | Apache-2.0 | https://github.com/espressif/esp-idf | `LICENSE` reproduce el texto Apache-2.0 sin titular propio; los ficheros fuente llevan cabeceras por fichero (conservarlas). No se usa directamente: viene dentro del core |
| Arduino-ESP32 core | **4.20017.260907+sha.dcc1105b** (resuelto por el pin `espressif32 @ 7.1.3`) | **LGPL-2.1-or-later** (SPDX declarado por el paquete del core; excepción aprobada, ver abajo) | https://github.com/espressif/arduino-esp32 | `LICENSE.md` (26.335 B): «GNU LESSER GENERAL PUBLIC LICENSE Version 2.1» con el preámbulo `Copyright (C) 1991, 1999 Free Software Foundation, Inc.`; el `package.json` del core declara `"license": "LGPL-2.1-or-later"` |
| mbedTLS (fork de Espressif incluido en el core) | la incluida en el core 4.4.7 | Apache-2.0 (salvo indicación específica por fichero) | https://github.com/espressif/mbedtls | `LICENSE` (135 B): «Unless specifically indicated otherwise in a file, files are licensed under the Apache 2.0 license, as can be found in: apache-2.0.txt» |
| ArduinoJson | **7.4.3** (2026-03-02) — **APROBADA y fijada**: `bblanchon/ArduinoJson@7.4.3` | MIT | https://github.com/bblanchon/ArduinoJson | `Copyright © 2014-2026, Benoit BLANCHON` (`LICENSE.txt`, "The MIT License (MIT)"). Verificado en el registro de PlatformIO (owner `bblanchon`, licencia MIT). Ficha de alta: `docs/DEPENDENCIES.md` |
| `dart_agent_core` | **2.1.6** — **APROBADA y fijada**: `dart_agent_core: 2.1.6` en `app/pubspec.yaml` | MIT | https://github.com/memex-lab/dart_agent_core | `Copyright (c) 2025 Memex Lab` (`LICENSE`, «MIT License»). **Modo copiloto (opt-in)**: se distribuye dentro del **ejecutable/APK de la app**, **nunca** en el firmware. Ficha: `docs/DEPENDENCIES.md` |
| `flutter_secure_storage` | **11.2.0** — **APROBADA y fijada**: `flutter_secure_storage: 11.2.0` en `app/pubspec.yaml` | **BSD-3-Clause** (**no** MIT) | https://github.com/mogol/flutter_secure_storage | `LICENSE`: «BSD 3-Clause License» + `Copyright 2017 German Saprykin`. Verificado también en los tags de pub.dev (`license:bsd-3-clause`, `license:osi-approved`). **Almacén de credenciales del copiloto (opt-in)**: va dentro del **ejecutable/APK de la app**, **nunca** en el firmware. Ficha: `docs/DEPENDENCIES.md` |
| `sqflite` | **2.4.4** — **APROBADA y fijada**: `sqflite: 2.4.4` en `app/pubspec.yaml` | **BSD-2-Clause** | https://github.com/tekartik/sqflite | `LICENSE`: «BSD 2-Clause License» + `Copyright (c) 2019, Alexandre Roux Tekartik`. Verificado también en los tags de pub.dev (`license:bsd-2-clause`, `license:osi-approved`). Publicador **tekartik.com**. **Persistencia local del historial (FASE 4B.7)**: va dentro del **ejecutable/APK de la app**, **nunca** en el firmware. Ficha: `docs/DEPENDENCIES.md` |
| `pointycastle` | **3.9.1** — **APROBADA y fijada**: `pointycastle: 3.9.1` en `app/pubspec.yaml` | **MIT** | https://github.com/bcgit/pc-dart | `LICENSE`: `Copyright (c) 2000 - 2019 The Legion of the Bouncy Castle Inc.` + texto MIT. Verificado en la caché local de pub. Publicador/titular **The Legion of the Bouncy Castle Inc.** **Verificación de la firma ES256 (FASE 4B.1 revisada)**: va dentro del **ejecutable/APK de la app**, **nunca** en el firmware. Ficha: `docs/DEPENDENCIES.md` |

### Transitivas de la app que entran con `flutter_secure_storage` (almacén de credenciales)

| Paquete | Licencia | Titular / primera línea del `LICENSE` |
|---|---|---|
| `flutter_secure_storage_darwin` · `flutter_secure_storage_linux` · `flutter_secure_storage_web` · `flutter_secure_storage_windows` · `flutter_secure_storage_platform_interface` | **BSD-3-Clause** (mismo proyecto) | `Copyright 2017 German Saprykin` |

> En **Linux** el plugin usa **libsecret** (Secret Service), que es una dependencia **del sistema**: la
> aporta la distribución y **no** se empaqueta con la app. Si no hay servicio de secretos, el guardado
> **falla y se declara**; no hay copia en claro de repuesto.

### Transitivas de la app que entran con `dart_agent_core` (modo copiloto)

Licencias **verificadas** en los ficheros `LICENSE` de la caché local de pub (2026-09-23); las versiones
resueltas están en `app/pubspec.lock`.

| Paquete | Licencia | Titular / primera línea del `LICENSE` |
|---|---|---|
| `aws_common` · `aws_signature_v4` | Apache-2.0 | «Apache License» (texto completo en su `LICENSE`) |
| `crypto` · `http` · `logging` · `http2` · `os_detect` · `stream_transform` · `json_annotation` · `fixnum` · `typed_data` · `mime` · `convert` | **BSD-3-Clause** (texto `Redistribution and use…` **con** la cláusula de no respaldo) | Copyright the Dart project authors (2013-2017) |
| `built_value` · `built_collection` | **BSD-3-Clause** | Copyright 2015, Google Inc. All rights reserved. |
| `dio` · `dio_web_adapter` · `mcp_dart` | MIT | «MIT License» |
| `uuid` | MIT (`Permission is hereby granted…`) | Copyright (c) 2021 Yulian Kuncheff |

> Estas transitivas **no** las elige el proyecto: las arrastra `dart_agent_core`. Se reproducen aquí porque
> la app se distribuye en binario; si alguna cambiara de licencia, la revisión de la política (§HARNESS
> «POLÍTICA DE LICENCIAS») se repite **antes** de publicar una versión.

### Transitivas de la app que entran con `sqflite` (FASE 4B)

Licencias **verificadas** en los ficheros `LICENSE` de la caché local de pub (2026-09-30); las versiones
resueltas están en `app/pubspec.lock`.

| Paquete | Licencia | Titular / primera línea del `LICENSE` |
|---|---|---|
| `sqflite_android` · `sqflite_darwin` · `sqflite_common` · `sqflite_platform_interface` | **BSD-2-Clause** (mismo proyecto tekartik) | `Copyright (c) 2019, Alexandre Roux Tekartik` |
| `path` | **BSD-3-Clause** | Copyright the Dart project authors |
| `crypto` · `typed_data` · `collection` | **BSD-3-Clause** (texto `Redistribution and use…` **con** la cláusula de no respaldo) | Copyright the Dart project authors (2013-2017) |
| `ffi` · `meta` | **BSD-3-Clause** | Copyright the Dart project authors |

> `sqflite_common_ffi` **2.4.3** (BSD-2-Clause, `tekartik/sqflite`) es **solo `dev_dependency`**: no entra en
> el APK. Arrastra `sqlite3` (MIT — `simonbinder.eu`), `synchronized` (MIT — `tekartik.com`) y `meta`/`path`.
> En **Linux** los tests usan **SQLite del sistema** (`libsqlite3-0`/`libsqlite3-dev`), que aporta la
> distribución y **no** se empaqueta con la app.

## Estado de aprobación

- **Aprobadas**: PlatformIO Core, PlatformIO platform `espressif32`, ESP-IDF, Arduino-ESP32
  core (con la excepción LGPL-2.1 documentada en `docs/HARNESS.md`).
- **Aprobada tras verificación de licencia**: mbedTLS (Apache-2.0 en el fork de Espressif).
- **Aprobada e INCORPORADA AL BINARIO (2026-09-22)**: ArduinoJson **7.4.3** (MIT) — ficha en
  `docs/DEPENDENCIES.md`; declarada con **versión exacta** en `firmware/platformio.ini` (entornos
  `esp32dev` y `native`) al implementar `serial_bridge`, que es el módulo que la usa.
- **Aprobada e INCORPORADA (2026-09-23, app)**: `dart_agent_core` **2.1.6** (MIT) y
  `flutter_secure_storage` **11.2.0** (**BSD-3-Clause**) — **solo modo copiloto (opt-in)** y **solo**
  dentro de `app/`; el firmware no las usa ni las conoce (`docs/HARNESS.md`, «EXCEPCIÓN IA EN RUNTIME —
  MODO COPILOTO (opt-in)»). Fichas: `docs/DEPENDENCIES.md`.
- **Aprobadas para la FASE 4B (2026-09-30, app — modo determinista)**: `sqflite` **2.4.4** (BSD-2-Clause)
  y `sqflite_common_ffi` **2.4.3** (BSD-2-Clause, **solo `dev_dependency`**). Fichas:
  `docs/DEPENDENCIES.md`.
- **Aprobada para 4B.1 revisada (2026-09-30, app — firma ES256)**: `pointycastle` **3.9.1** (MIT),
  sustituta de `cryptography 2.9.0`, que no tenía backend Dart/Linux funcional para ECDSA P-256. Ficha:
  `docs/DEPENDENCIES.md`.
- **Fijado (2026-09-22)**: `firmware/platformio.ini` fija `platform = espressif32 @ 7.1.3`, que
  resuelve Arduino-ESP32 core `4.20017.260907+sha.dcc1105b` (con IDF **4.4.7** dentro) y el resto
  del toolchain. Cualquier cambio de pin obliga a revisar esta tabla.

## Cumplimiento LGPL-2.1 del core Arduino-ESP32

El core `espressif/arduino-esp32` se enlaza estáticamente en el firmware. Para cumplir la
obligación de *relink* de LGPL-2.1 §6, el proyecto se compromete a:

1. **No modificar** el core (se usa tal como lo entrega la plataforma).
2. Reproducir estos avisos en la documentación del producto distribuido.
3. Facilitar la reconstrucción del firmware con una versión modificada del core (mismo
   toolchain y `platformio.ini` publicado), de modo que el usuario pueda sustituirlo.

## Componentes NO incluidos (y por qué)

| Componente | Motivo de exclusión |
|---|---|
| `ciniml/WireGuard-ESP32-Arduino` | BSD-3-Clause ✅ pero **sin actividad desde 2024-04-01** → incumple la regla 3 de la política |
| `euginfrancis/ESP32_JWT_Auth` | **Sin fichero de licencia** ⇒ todos los derechos reservados: no es usable |
| `isiy0/ESP32-Deauther-EvilTwin` (base) | **GPL-3.0** → no se reutiliza código; solo referencia de comportamiento (protocolo clean-room) |

> Nota: los textos de copyright se han copiado literalmente de los ficheros de licencia
> verificados el **2026-09-22**. Este documento no sustituye el asesoramiento jurídico.
