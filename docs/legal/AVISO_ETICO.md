# AVISO ÉTICO DE USO — Priverlo

Priverlo es una herramienta de **auditoría de seguridad** pensada para que una persona revise **sus
propios** dispositivos y **su propia** red local. Este aviso se acepta **antes** de usar la aplicación
(la aceptación queda registrada en el dispositivo, con **fecha y versión** de este texto).

## 1. Solo sobre lo que es tuyo, o sobre lo que tengas permiso escrito

- Audita **tus** dispositivos y **tu** red.
- Auditar equipos o redes de terceros **sin autorización expresa** puede ser **delito** en tu país,
  aunque no llegues a modificar nada. La responsabilidad es de **quien usa** la herramienta.
- Si trabajas como profesional, ten el **encargo por escrito** (alcance, ventana de tiempo y persona de
  contacto) **antes** de empezar.

## 2. Qué hace y qué NO hace esta aplicación

- La **app** solo realiza comprobaciones **locales y de lectura**: revisa el estado del dispositivo y
  enumera la red local (nombre, dirección física, canal, seguridad…) para **informar**.
- Las funciones de **radio y de ataque** (desautenticación, *evil twin*, portal cautivo, etc.) viven en
  el **firmware de un accesorio aparte** y **no** se distribuyen con esta aplicación.
- **Nada** se envía a ningún servidor: no hay telemetría y los datos se quedan en el dispositivo. La
  única excepción es el **copiloto**, y solo si tú lo activas: lo que escribas va al proveedor que tú
  elijas y con tu clave.

## 3. Sin garantías

- El software se entrega **«tal cual»**, sin garantía de ningún tipo (véase `LICENSE`).
- Los hallazgos son **indicios**, no un dictamen: una comprobación «no disponible» **no** significa que
  el dispositivo esté bien, y la ausencia de hallazgos **no** certifica nada.
- Es una ayuda para **tu criterio**, nunca un sustituto: la decisión y la responsabilidad son tuyas.

## 4. Datos personales

- La app trata datos de **tu** dispositivo y guarda el historial **en él** (SQLite local). Si el equipo
  es de otra persona, necesitas una **base legítima** para tratar sus datos antes de auditarlo.

---

*Versión de este aviso: **v1** (2026-10-02). Si el texto cambia, la aplicación volverá a pedir la
aceptación: quedará registrado que aceptaste **este** texto, no el siguiente.*
