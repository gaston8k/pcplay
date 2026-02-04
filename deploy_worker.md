# Instrucciones para desplegar Cloudflare Worker

## 1. Requisitos previos
- Cuenta en Cloudflare (gratuita)
- Acceso a Cloudflare Dashboard (https://dash.cloudflare.com)
- Tu proyecto Supabase ya configurado con la vista `public_photos_view`

## 2. Crear un nuevo Worker
1. Ve a **Workers & Pages** en el dashboard de Cloudflare.
2. Haz clic en **Create application** > **Create Worker**.
3. Asigna un nombre al Worker, por ejemplo `fotomap-proxy`.
4. Elige un subdominio (ej: `fotomap-proxy.<tu-usuario>.workers.dev`).
5. En la pestaña **Code**, borra el código por defecto y pega el contenido de `web/fotomap-worker.js`.
6. Haz clic en **Save and deploy**.

## 3. Verificar el despliegue
- Una vez desplegado, visita la URL del Worker (ej: `https://fotomap-proxy.<tu-usuario>.workers.dev/health`).
- Deberías ver `{"status":"ok","worker":"fotomap-proxy"}`.
- Prueba el endpoint de fotos: `https://fotomap-proxy.<tu-usuario>.workers.dev/api/photos`.
- Debería devolver un JSON con las fotos públicas.

## 4. Configurar CORS (opcional)
El Worker ya incluye headers CORS para permitir cualquier origen (`*`). Si quieres restringir a tu dominio, modifica la constante `CORS_HEADERS` en el código.

## 5. Actualizar el visualizador web
Una vez que el Worker esté funcionando, debes modificar el archivo `web/fotomap_viewer_final.html` para que use el Worker en lugar de Supabase directamente.

### Cambios necesarios:
1. Abre `web/fotomap_viewer_final.html`.
2. Busca la constante `CONFIG` (líneas 447-451) y reemplázala con:
```javascript
const CONFIG = {
    WORKER_URL: 'https://fotomap-proxy.<tu-usuario>.workers.dev/api/photos',
    R2_PUBLIC_URL: 'https://fotomap.pcplay.com.ar'
};
```
3. Busca la función `loadPhotosFromSupabase` (línea 550) y reemplaza la llamada fetch por:
```javascript
const response = await fetch(CONFIG.WORKER_URL);
```
4. Elimina los headers `apikey` y `Authorization` (ya no son necesarios).
5. Ajusta el mapeo de datos si es necesario (el Worker ya devuelve el formato esperado).

**Nota:** He preparado una versión actualizada del visualizador que puedes usar directamente: `web/fotomap_viewer_worker.html`.

## 6. Desplegar visualizador actualizado
- Sube los archivos HTML, CSS, JS a GitHub Pages o a tu servidor web.
- Asegúrate de que el Worker esté accesible desde el dominio del visualizador (mismo origen o CORS configurado).

## 7. Solución de problemas
- **Error 500:** Verifica que las credenciales de Supabase en el Worker sean correctas.
- **Error 404:** Asegúrate de que la vista `public_photos_view` exista y tenga datos.
- **CORS:** Si el visualizador no puede acceder al Worker, revisa los headers CORS.

## 8. Recursos
- [Documentación de Cloudflare Workers](https://developers.cloudflare.com/workers/)
- [Supabase REST API](https://supabase.com/docs/reference/javascript/select)

## 9. Archivos proporcionados
- `web/fotomap-worker.js` - Código del Worker
- `web/fotomap_viewer_worker.html` - Visualizador actualizado (si existe)
- `web/deploy_worker.md` - Estas instrucciones

¡Listo! Con esto tus credenciales de Supabase estarán protegidas y el visualizador funcionará de forma escalable.