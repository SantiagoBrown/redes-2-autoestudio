# 📡 Redes 2 · Ruta de autoestudio

Aplicación web interactiva de **un solo archivo** (`index.html`) para estudiar Redes 2 paso a paso. Está construida con **React 18 + Tailwind CSS**, funciona como una ruta guiada y usa tres técnicas de estudio:

- **Microlearning:** cada módulo se divide en teoría breve, video y práctica.
- **Técnica Feynman:** explicaciones con analogías cotidianas y un espacio para que expliques el tema con tus palabras.
- **Active Recall:** 3 preguntas por módulo con corrección y justificación instantáneas.

---

## 🚀 Cómo abrirla

1. Abre la carpeta `recursos de aprendizaje`.
2. Haz doble clic en `index.html` (o ábrelo con Chrome, Edge, Brave o Firefox).
3. Listo. Los videos se cargan desde la misma carpeta.

> **Nota:** React, Tailwind y Babel se cargan desde CDN, así que la primera carga necesita conexión a Internet. Después el navegador puede usar la caché. Los videos y el progreso son 100 % locales.

---

## 🗺️ La ruta

| Módulo | Tema | Práctica |
| --- | --- | --- |
| 01 | Conmutación de Capa 2 / Switching (MAC, VLAN, 802.1Q, EtherChannel, DTP) | 3 preguntas |
| 02 | Spanning Tree (STP, RSTP, PVST+, PortFast, BPDU Guard) | 3 preguntas |
| 03 | Redes WAN (topologías, PPP/HDLC, GRE, NAT, MPLS, DMVPN) | 3 preguntas |
| 04 | Calidad de Servicio (DSCP, colas, policing/shaping) | 3 preguntas |
| 05 | IPv6 (formato, link-local, NDP, SLAAC, Dual Stack) | 3 preguntas |
| 06 | Automatización y Gestión (SDN, DNA Center, REST, SNMP, Syslog) | 3 preguntas |
| 07 | Integración WAN (troncales, GRE, Metro Ethernet, SD-WAN, MPLS) | 3 preguntas |
| 08 | Integración de Redes y VPN (sitio a sitio, acceso remoto, GRE/IPSec, IPv4/IPv6) | 3 preguntas |

Cada módulo tiene tres pasos: **Teoría → Video → Práctica**. El progreso se guarda en `localStorage` y el roadmap de la barra lateral muestra qué pasos ya completaste.

- Un módulo se considera completado cuando haces la teoría, ves el video (si existe) y apruebas la práctica con **2 de 3** respuestas correctas.
- El módulo 04 todavía no tiene grabación: el video es opcional y no bloquea el progreso. Si agregas el archivo, el reproductor aparece automáticamente.

---

## 🎥 Videos usados

Los nombres deben coincidir exactamente y estar en la misma carpeta que `index.html`.

| Módulo | Archivo | Estado |
| --- | --- | --- |
| 01 · Switching | `videog1.mp4` | Principal (Switching avanzado) |
| 02 · STP | `video2.mp4` | Principal (Spanning Tree) |
| 03 · WAN | `video3.mp4` | Principal (Redes WAN) |
| 04 · QoS | `video4-qos.mp4` | Opcional, pendiente de agregar |
| 05 · IPv6 | `modulo4-ipv6.mp4` | Principal (Fundamentos de IPv6) |
| 05 · IPv6 | `videog5.mp4` | Complemento (IPv6 en práctica) |
| 06 · Automatización | `video6.mp4` | Principal (Automatización y gestión) |
| 07 · Integración WAN | `video7.mp4` | Principal (Integración WAN) |
| 08 · VPN | `video8.mp4` | Principal (Integración y VPN) |

Para agregar el video de QoS, copia el archivo con el nombre `video4-qos.mp4`. No hace falta tocar el código.

---

## 🧠 Cómo estudiar con esta app

1. **Lee la analogía** antes de mirar los términos técnicos.
2. **Explica el tema en el cuadro Feynman** usando tus propias palabras, sin jerga.
3. **Mira el video** y marca el paso. Puedes pausar y anotar.
4. **Responde la práctica sin mirar arriba.** La app te corrige al instante y te dice por qué.
5. **Si fallas, vuelve a la analogía y reintenta.** El puntaje se guarda por módulo.
6. Repasa a los **1, 7 y 30 días** para aprovechar la repetición espaciada.

---

## 🛠️ Personalización

Todo el contenido vive en el arreglo `MODULES` dentro de `index.html`:

```js
const MODULES = [
  {
    id: 'l2',
    title: 'Conmutación de Capa 2',
    accent: '#38BDF8',
    analogy: '...',
    sections: [ ... ],
    videos: [ { src: 'videog1.mp4', label: '...' } ],
    quiz: [
      {
        question: '...',
        options: ['...', '...', '...', '...'],
        answer: 2,       // índice de la opción correcta (0 = A)
        why: '...'
      }
    ]
  }
];
```

Para agregar un módulo, copia un objeto, cambia su `id` y agrégalo al arreglo. La barra lateral, el progreso y la numeración se actualizan solos.

### Cambiar colores

Cada módulo tiene su acento en la propiedad `accent`. El fondo y la tipografía se configuran en `tailwind.config` y en el bloque `<style>` del mismo archivo.

---

## 💾 Progreso y reinicio

- Progreso: clave `redes2:progreso:v2` en `localStorage`.
- Último módulo abierto: clave `redes2:modulo-actual:v1`.
- Para borrar todo, usa **Reiniciar progreso** en la barra lateral o el icono de reinicio de la barra superior.

Si abres el archivo en modo incógnito, el progreso se perderá al cerrar la ventana.

---

## 📂 Archivos

```
recursos de aprendizaje/
├── index.html              ← toda la aplicación (React + Tailwind)
├── README.md
├── videog1.mp4             ← Módulo 01 (Switching)
├── video2.mp4              ← Módulo 02 (STP)
├── video3.mp4              ← Módulo 03 (WAN)
├── video4-qos.mp4          ← opcional, agrégalo para el Módulo 04 (QoS)
├── modulo4-ipv6.mp4        ← Módulo 05 (IPv6)
├── videog5.mp4             ← Módulo 05 (IPv6 complemento)
├── video6.mp4              ← Módulo 06 (Automatización)
├── video7.mp4              ← Módulo 07 (Integración WAN)
├── video8.mp4              ← Módulo 08 (VPN)
├── G1.pdf … G8.pdf         ← material de clase
├── recurso*.pdf
└── boceto-original/        ← versión anterior (HTML + CSS + JS separados)
```

La versión anterior quedó respaldada en `boceto-original/` por si quieres comparar o recuperar algo.

> **Repositorio:** solo se publican `index.html`, `README.md` y `.gitignore`. Los videos y PDFs permanecen en tu carpeta local y están excluidos mediante `.gitignore`.

---

## ❓ Problemas frecuentes

**No aparece nada / queda en “Cargando”.**  
Revisa tu conexión: la app necesita descargar React, Tailwind y Babel la primera vez. También puedes abrir la consola (F12) para ver el error.

**Un video no se reproduce.**  
Comprueba que el archivo esté en la misma carpeta y que el nombre coincida exactamente (mayúsculas incluidas). Usa MP4 con códec H.264.

**El progreso no se guarda.**  
No uses modo incógnito y permite el almacenamiento local para el archivo.

**Quiero empezar de cero.**  
Barra lateral → **Reiniciar progreso**.

---

Hecho para estudiar sin distracciones: **una idea, un video, una pregunta a la vez.**
