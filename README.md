# Daily Spending — PWA para iPhone

App independiente creada desde `calculadora_gastos_diarios(1).xlsx`. No necesita servidor, base de datos ni cuenta para guardar saldos, una vez publicada.

## Fórmulas originales preservadas

- `Gasto objetivo MTD = día del mes / días del mes`
- `Gasto real MTD = 1 - ((Edenred + Revolut) / presupuesto)`
- `Disponible para gastar hoy = presupuesto × (objetivo MTD - gasto real MTD)`

Presupuesto inicial: 500 €. Saldos iniciales: Edenred 246,50 €, Revolut 183,10 €. Se incluye un primer registro de ejemplo fechado 2026-11-08, procedente del archivo adjunto. La fecha del formulario se ajusta al día actual del dispositivo.

**Importante:** El indicador «Disponible para gastar hoy» equivale matemáticamente al *margen acumulado contra el ritmo previsto* hasta la fecha, no a una cuota segura para un único día. Los saldos solo cambian cuando los editas; no hay integración bancaria.

## Cómo publicarla gratis con GitHub Pages

1. Inicia sesión en https://github.com e introduce un repositorio nuevo, por ejemplo `daily-spending` (elige **Public** si usas GitHub Free).
2. Extrae el ZIP de este proyecto y sube **todo su contenido** directamente a la raíz del repositorio (`index.html`, `app.js`, `styles.css`, `sw.js`, `manifest.webmanifest`, `.nojekyll` y la carpeta `icons`). No subas la carpeta contenedora como subcarpeta.
3. En el repositorio abre **Settings → Pages → Build and deployment**.
4. Selecciona **Deploy from a branch** → `main` → `/(root)` y guarda.
5. GitHub mostrará la URL de tu sitio. Suele ser `https://TU-USUARIO.github.io/daily-spending/` (confirma la URL real en Pages).
6. Abre la URL en **Safari** desde el iPhone → botón Compartir → **Añadir a pantalla de inicio** → activa **Abrir como app web** si aparece → **Añadir**.
7. Abre el icono. Una vez cargada por primera vez, podrás utilizar la app sin conexión.

La URL y los archivos HTML/CSS/JS son públicos en GitHub Pages; **tus saldos y el historial no se suben a GitHub**: se guardan en el almacenamiento local del iPhone.

## Uso diario

- La fecha se carga automáticamente con el día actual.
- Actualiza los saldos de Edenred y Revolut. Los indicadores cambian al escribir.
- Pulsa **Guardar saldos** para guardarlos y crear/actualizar un registro de ese día.
- Puedes revisar y volver a cargar registros anteriores.
- En Ajustes, actualiza el presupuesto mensual.
- Usa **Exportar respaldo** para descargar un JSON con tus datos; **Importar respaldo** restaura ese JSON. **Exportar CSV** permite abrir el historial en Excel (no sustituye el respaldo JSON).

## Limitaciones y privacidad

- No hay sincronización entre iPhone y ordenador ni copia de seguridad en la nube.
- El almacenamiento es local al navegador/app y al dispositivo. Borrar el contenido web, reinstalar o perder el dispositivo podría borrar los datos; exporta respaldos con frecuencia y guárdalos en Archivos/iCloud Drive.
- Es posible que Safari y el icono instalado mantengan almacenamientos separados según versión/configuración: usa siempre el icono instalado para registrar tus saldos.
- Si cambias la URL/dominio, las entradas guardadas en el origen antiguo no se transfieren automáticamente: exporta/importa un JSON.
- El diseño se adapta a iPhone. No pide datos de acceso a Edenred ni Revolut; se introducen los saldos a mano.
- Para probar offline: visita la URL con Internet, espera a que cargue, luego activa modo avión y abre la app instalada.

## Probar localmente en un ordenador

Ejecuta `python3 -m http.server 8000` dentro de la carpeta descomprimida y abre `http://localhost:8000`. Abrir `index.html` con doble clic (`file://`) no prueba correctamente el modo offline.
