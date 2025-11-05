═══════════════════════════════════════════════════════════
   OFERTAS ML HUB - PAQUETE COMPLETO
   Sistema de Gestión de Ofertas de Mercado Libre
═══════════════════════════════════════════════════════════

📦 CONTENIDO DEL PAQUETE
────────────────────────────────────────────────────────────
✓ index.html          - Sitio web público
✓ app.js              - Lógica de la aplicación
✓ manifest.json       - Configuración PWA
✓ service-worker.js   - Funcionamiento offline
✓ README.txt          - Este archivo

═══════════════════════════════════════════════════════════
🚀 INSTALACIÓN RÁPIDA (5 MINUTOS)
═══════════════════════════════════════════════════════════

OPCIÓN 1: USAR LOCALMENTE (MÁS FÁCIL)
────────────────────────────────────────────────────────────
1. Extrae todos los archivos en una carpeta
   Ejemplo: C:\ofertas-ml-hub\

2. Abre "index.html" con tu navegador
   - Doble click en index.html
   - O arrastra el archivo al navegador

3. ¡LISTO! Ya funciona

4. OPCIONAL - Instalar como aplicación:
   - Chrome: Click en icono ⊕ en barra de direcciones
   - Edge: Igual que Chrome
   - Firefox: Agregar a favoritos


OPCIÓN 2: SUBIR A INTERNET (NETLIFY)
────────────────────────────────────────────────────────────
1. Ve a https://www.netlify.com

2. Crea cuenta gratis (con email o GitHub)

3. Arrastra TODA la carpeta a Netlify
   (No solo index.html, toda la carpeta)

4. Netlify te da una URL gratis:
   https://tu-sitio.netlify.app

5. ¡Listo! Tu sitio está en internet


OPCIÓN 3: GITHUB PAGES (GRATIS)
────────────────────────────────────────────────────────────
1. Crea cuenta en https://github.com

2. Crea nuevo repositorio "ofertas-ml-hub"

3. Sube todos los archivos

4. Settings → Pages → Enable

5. Tu URL: https://tu-usuario.github.io/ofertas-ml-hub


═══════════════════════════════════════════════════════════
⚙️ CONFIGURACIÓN INICIAL
═══════════════════════════════════════════════════════════

1. AGREGAR PRODUCTOS
────────────────────────────────────────────────────────────
   a) Abre el sitio
   b) Click en botón "⚙️ Admin"
   c) Llena el formulario:
      - Emoji: 📱
      - Nombre: iPhone 15 Pro
      - Categoría: Tecnología
      - Precio actual: 18999
      - Precio original: 25999
      - URL: https://articulo.mercadolibre...
   d) Click "Agregar Producto"
   e) ¡Aparece en el sitio!


2. OBTENER LINKS DE AFILIADO ML
────────────────────────────────────────────────────────────
   a) Regístrate en:
      https://afiliados.mercadolibre.com.mx
   
   b) Llena el formulario
   
   c) Espera aprobación (24-48 hrs)
   
   d) Genera links de afiliado:
      - Copia URL del producto en ML
      - Pega en generador de afiliados
      - Copia tu link único
      - Úsalo en el formulario


3. CONECTAR REDES SOCIALES
────────────────────────────────────────────────────────────
   En desarrollo - Próxima versión


═══════════════════════════════════════════════════════════
🎯 CÓMO USAR
═══════════════════════════════════════════════════════════

AGREGAR PRODUCTOS
────────────────────────────────────────────────────────────
1. Click en "⚙️ Admin"
2. Llenar formulario
3. Click "Agregar Producto"


FILTRAR PRODUCTOS
────────────────────────────────────────────────────────────
1. Click en botones de categoría:
   - Todos
   - Tecnología
   - Hogar
   - Moda
   - Deportes


VER ESTADÍSTICAS
────────────────────────────────────────────────────────────
1. Abre consola del navegador (F12)
2. Escribe: window.ofertasML.stats()
3. Ver todas las estadísticas


EXPORTAR DATOS
────────────────────────────────────────────────────────────
1. Consola: window.ofertasML.exportar()
2. Se descarga archivo JSON
3. Guárdalo como backup


═══════════════════════════════════════════════════════════
💾 DATOS Y ALMACENAMIENTO
═══════════════════════════════════════════════════════════

DÓNDE SE GUARDAN LOS DATOS
────────────────────────────────────────────────────────────
→ localStorage del navegador
→ Persiste incluso cerrando el navegador
→ Solo se borran si limpias datos del navegador


HACER BACKUP
────────────────────────────────────────────────────────────
Opción 1: Consola
   window.ofertasML.exportar()

Opción 2: Manual
   1. F12 → Application → Local Storage
   2. Copiar valor de "ofertasMLData"
   3. Guardar en archivo .txt


RESTAURAR BACKUP
────────────────────────────────────────────────────────────
1. F12 → Console
2. Pega el JSON guardado
3. Recarga la página


═══════════════════════════════════════════════════════════
🔧 PERSONALIZACIÓN
═══════════════════════════════════════════════════════════

CAMBIAR COLORES
────────────────────────────────────────────────────────────
Edita index.html, busca:
<style>
    body {
        background: linear-gradient(...);
    }
</style>

Cambia los colores a tu gusto


CAMBIAR LOGO/EMOJI
────────────────────────────────────────────────────────────
Busca: <h1>🔥 <span class="highlight">OFERTAS</span>
Cambia 🔥 por tu emoji o logo


AGREGAR CATEGORÍAS
────────────────────────────────────────────────────────────
1. Busca en index.html:
   <select id="category">

2. Agrega nueva opción:
   <option value="nueva">Nueva Categoría</option>

3. Agrega botón de filtro:
   <button class="filter-btn" 
           onclick="filterProducts('nueva')">
       Nueva Categoría
   </button>


═══════════════════════════════════════════════════════════
📱 USAR COMO APP EN CELULAR
═══════════════════════════════════════════════════════════

ANDROID (Chrome)
────────────────────────────────────────────────────────────
1. Abre el sitio en Chrome
2. Menú (⋮) → "Instalar aplicación"
3. Aparece icono en pantalla de inicio


iOS (Safari)
────────────────────────────────────────────────────────────
1. Abre el sitio en Safari
2. Botón compartir
3. "Agregar a pantalla de inicio"


═══════════════════════════════════════════════════════════
❓ SOLUCIÓN DE PROBLEMAS
═══════════════════════════════════════════════════════════

"No se guardan los productos"
────────────────────────────────────────────────────────────
→ Verifica que no estés en modo incógnito
→ Permite cookies en configuración del navegador


"No puedo instalar como app"
────────────────────────────────────────────────────────────
→ Usa Chrome o Edge
→ El sitio debe estar en HTTPS (Netlify lo hace automático)
→ O simplemente úsalo en el navegador normal


"Los productos no aparecen"
────────────────────────────────────────────────────────────
→ F12 → Console → Busca errores
→ Recarga la página (Ctrl+F5)
→ Verifica que app.js esté cargado


"Quiero empezar de cero"
────────────────────────────────────────────────────────────
Opción 1: Consola
   window.ofertasML.limpiar()

Opción 2: Manual
   1. F12 → Application → Local Storage
   2. Click derecho → Clear
   3. Recarga página


═══════════════════════════════════════════════════════════
🌟 PRÓXIMAS FUNCIONES
═══════════════════════════════════════════════════════════

✓ Panel de administración completo
✓ Exportar/Importar datos
✓ Funciona offline
✓ Instalar como app

🔜 En desarrollo:
   → Integración con redes sociales
   → Generación automática de posts
   → Estadísticas avanzadas
   → Sincronización en la nube
   → Notificaciones push
   → Comparador de precios
   → Historial de precios
   → Alertas de ofertas


═══════════════════════════════════════════════════════════
📞 SOPORTE
═══════════════════════════════════════════════════════════

Si tienes dudas o problemas:

1. Revisa este README completo
2. Verifica la consola del navegador (F12)
3. Asegúrate de tener la última versión
4. Prueba en otro navegador


═══════════════════════════════════════════════════════════
📝 COMANDOS DE CONSOLA ÚTILES
═══════════════════════════════════════════════════════════

Ver todos los productos:
   window.ofertasML.productos()

Ver estadísticas:
   window.ofertasML.stats()

Exportar datos:
   window.ofertasML.exportar()

Limpiar todo:
   window.ofertasML.limpiar()


═══════════════════════════════════════════════════════════
✅ CHECKLIST DE INSTALACIÓN
═══════════════════════════════════════════════════════════

□ Extraer todos los archivos
□ Abrir index.html en navegador
□ Verificar que carga correctamente
□ Agregar primer producto de prueba
□ Verificar que se guarda (recargar página)
□ (Opcional) Subir a Netlify/GitHub
□ (Opcional) Instalar como PWA
□ Registrarse en afiliados ML
□ Esperar aprobación
□ Generar primeros links de afiliado
□ Agregar productos reales
□ ¡Empezar a compartir y ganar!


═══════════════════════════════════════════════════════════
🎉 ¡LISTO PARA USAR!
═══════════════════════════════════════════════════════════

Versión: 1.0.0
Fecha: Noviembre 2025
Licencia: Uso libre

¡Éxito con tus ofertas! 🚀🔥💰