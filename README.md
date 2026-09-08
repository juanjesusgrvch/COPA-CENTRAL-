<div align="center">
  <img src="ESCUDO.png" alt="Escudo Club Atlético Central Norte" width="150"/>
  <h1>🏆 Sistema de Inscripción - Copa Central 2026</h1>
  <p><em>Aplicación Web (SPA) para la gestión automatizada de jugadores y generación de carnets deportivos.</em></p>
</div>

---

## El Valor de la Digitalización

La transición de un modelo de inscripción tradicional en papel a este ecosistema digital interactivo representa un salto cualitativo vital en la gestión del torneo. A nivel **organizativo**, elimina la pérdida de documentos físicos, los problemas de caligrafía ilegible y centraliza la información en un formato estandarizado e inmutable. En términos de **administración**, automatiza el 100% de la validación de reglas de negocio (como el cálculo de rangos de edades permitidas y campos obligatorios), reduciendo drásticamente la carga operativa y los tiempos de revisión del staff. Desde una perspectiva de **marketing**, proyecta una imagen institucional moderna, seria y profesional del Club Atlético Central Norte, elevando el prestigio del evento y generando mayor confianza en los colegios participantes y potenciales patrocinadores.

## Características Técnicas e Implementaciones

Este proyecto fue desarrollado bajo una arquitectura *Serverless/Client-Side* pura, asegurando máxima disponibilidad y cero costos de infraestructura backend.

* **Motor de Estilos:** Construido con **Tailwind CSS** para un diseño *Mobile-First*, responsivo y escalable, acompañado de **Lucide Icons** para una iconografía limpia y consistente.
* **Motor PDF (Bypass Print):** Integración de `jsPDF` y `html2canvas` para procesar el DOM y renderizar un lienzo (*Canvas*) de alta resolución. Esto garantiza una exportación de PDF en tamaño A4 matemático (210x297mm) *Pixel-Perfect*, solucionando las discrepancias de impresión entre distintos navegadores y sistemas operativos (problema N°1 en desfase de documentos).
* **Geometría SVG Nativa:** Reemplazo de reglas CSS por vectores SVG inyectados dinámicamente para asegurar que los diseños de los carnets no pierdan fidelidad al ser empaquetados en el PDF.
* **Persistencia de Estado (Drafting):** Implementación de `localStorage` para guardar en tiempo real el progreso del usuario (Autosave). Previene la pérdida de datos ante recargas o cierres accidentales de la pestaña.
* **Seguridad y Accesibilidad:** Inclusión de un campo *Honeypot* invisible para mitigar ataques de Spam por bots, y un diseño enfocado en contrastes legibles (WCAG).
* **Experiencia de Usuario (UX):** Flujo protegido por un Modal interceptor de Términos y Condiciones, validación visual de errores (`shake animation`) y un *Dev Trigger* (clic triple en el título) para autocompletar datos durante fases de Testing/QA.

## Flujo de Funcionamiento

1. **Captura de Datos:** El delegado completa el formulario principal con la información del colegio, nombre del equipo y la nómina de hasta 16 jugadores más 1 responsable.
2. **Validación en Tiempo Real:** El sistema sanitiza los *inputs* (forzando mayúsculas y formatos numéricos) y verifica que los años de nacimiento cumplan con el reglamento del torneo.
3. **Acuerdo de Términos:** Al intentar generar los carnets, se despliega un modal bloqueante que exige la lectura y aceptación explícita de las Obligaciones y Responsabilidades Civiles.
4. **Renderizado UI:** La interfaz oculta el formulario y genera dos vistas previas interactivas: Los carnets individuales (Frente y Reverso generados dinámicamente) y la Lista de Buena Fe tabular para fiscalización.
5. **Exportación:** Mediante un solo clic, se unifican todas las vistas en un único archivo `.pdf` en formato A4 listo para ser impreso o enviado a la organización.