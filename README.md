# 📱 Catálogo de Accesorios - CELUCENTER

**Herramienta profesional para vendedores internos de CELUCENTER**

Un catálogo interactivo y dinámico que se conecta directamente con tu Google Sheet, permitiendo gestionar productos, precios y favoritos sin necesidad de actualizar código.

---

## 🎯 Características

✅ **Conexión segura a Google Sheets** mediante Google Apps Script (sin exponer datos públicamente)

✅ **Búsqueda en tiempo real** por código o nombre de producto

✅ **Filtrado por categoría** para organizar mejor el catálogo

✅ **Dos vistas disponibles**
  - Vista Grid (2 columnas)
  - Vista Lista (información expandida)

✅ **Sistema de favoritos** guardado localmente para acceso rápido

✅ **Cálculo automático de precios**
  - Precio Lista F (precio base)
  - Precio Público (190% de Lista F)

✅ **Botones de acción rápida**
  - Copiar código del producto
  - Copiar información completa (código, nombre y precios)
  - Marcar como favorito

✅ **Imágenes optimizadas** que se cargan desde GitHub

✅ **Interfaz responsive** - Funciona en desktop, tablet y móvil

✅ **Confirmaciones visuales** con notificaciones tipo toast

✅ **Ordenamiento flexible** por nombre, código o categoría

---

## 🚀 Cómo usar

### 1. Descargar el archivo
Descarga `catalogo_accesorios_v2.html` y abre en tu navegador favorito.

### 2. Los datos se cargan automáticamente
El catálogo se conecta a tu Google Sheet mediante el Google Apps Script y trae todos los productos, precios e imágenes.

### 3. Características principales

**Búsqueda:**
- Escribe en la barra de búsqueda para encontrar productos por código o nombre
- La búsqueda es instantánea mientras escribes

**Filtros:**
- Filtra por categoría usando el selector de categorías
- Limpia los filtros rápidamente con el botón "Limpiar filtros"

**Vista:**
- Cambia entre vista Grid (2 columnas) o Lista (información expandida)

**Favoritos:**
- Haz clic en la estrella para marcar productos favoritos
- Los favoritos se guardan automáticamente en tu navegador
- El contador muestra cuántos favoritos tienes guardados

**Copiar información:**
- Haz clic en el código del producto para copiar solo el código
- Usa el botón "Copiar código" para lo mismo
- Usa "Copiar info" para copiar código, nombre y ambos precios

**Ordenamiento:**
- Ordena los productos por nombre (A-Z), código o categoría
- Los productos se reorganizan instantáneamente

---

## 📊 Estructura de datos (Google Sheet)

El catálogo lee automáticamente de tu Google Sheet con esta estructura:

| Columna | Campo | Ejemplo |
|---------|-------|---------|
| A | Código | `GAR142` |
| B | Nombre | `COMBO CARGADOR TIPO C 1M 2.4A 12W MAX` |
| C | Nombre en STX | (no se usa) |
| D | Categoria STX | (no se usa) |
| E | Categoría | `COMBO CARGADORES` |
| F-I | (varios) | (no se usa) |
| J | Lista M | (no se usa en esta versión) |
| K | Lista G | (no se usa en esta versión) |
| L | Lista F | `37.10` |
| M | Precio Público | (calculado automáticamente) |
| N | Archivo (imagen) | `GAR142.png` |

**Importante:** Solo se mostrarán productos que tengan **código (columna A) y nombre (columna B)** válidos.

---

## 🔐 Configuración de seguridad

### Google Apps Script
El catálogo usa Google Apps Script para servir datos de forma segura:

1. **La hoja NO es pública** - Solo el Apps Script accede a los datos
2. **Autenticación por token** - Se requiere un token válido para acceder
3. **Datos filtrados** - Solo se envía lo necesario (códigos, nombres, precios, imágenes)

**Token por defecto:** `CELUCENTER_SECURE_2025`

Puedes cambiar el token en el Google Apps Script si lo deseas.

---

## 🖼️ Imágenes

Las imágenes se cargan automáticamente desde GitHub:

```
https://raw.githubusercontent.com/piztian/Accesorios-Celucenter/main/fotos/
```

Los nombres de archivo vienen del campo "Archivo" en tu Google Sheet (columna N).

**Ejemplo:** Si pones `GAR142.png`, el catálogo buscará:
```
https://raw.githubusercontent.com/piztian/Accesorios-Celucenter/main/fotos/GAR142.png
```

---

## 💾 Datos locales

El catálogo guarda automáticamente:
- **Favoritos** - Guardados en localStorage del navegador
- Puedes borrar el historial de navegación para limpiar los favoritos

---

## 🎨 Personalización

### Cambiar colores
En el archivo HTML, busca la sección `:root`:

```css
:root {
    --celucenter-red: #E31837;
    --celucenter-blue: #003087;
    --celucenter-red-light: #ff1a4a;
    --celucenter-blue-light: #0047cc;
}
```

Modifica los valores hexadecimales para cambiar los colores del sitio.

### Cambiar el margen de ganancia (190%)
En el HTML, busca `1.9` en dos lugares:
1. En la línea donde calcula el Precio Público (línea ~814)
2. En la función de copiar información (línea ~883)

Cambia `1.9` a tu valor deseado (ej: `2.0` para 200%, `1.5` para 150%, etc.)

### Cambiar token de seguridad
1. Ve al Google Apps Script
2. Busca `"CELUCENTER_SECURE_2025"`
3. Reemplázalo por tu token personalizado
4. En el HTML, en la URL del Apps Script, cambia el parámetro `token=` al nuevo valor

---

## 🐛 Solución de problemas

**P: El catálogo muestra "Error al cargar datos"**
- Verifica que tu Google Sheet esté compartido (Compartir → Cualquiera con el link)
- Verifica que la pestaña se llame exactamente "CatalogoCC"
- Verifica tu conexión a internet
- Presiona F12 → Consola para ver el error específico

**P: Las imágenes no aparecen**
- Verifica que el archivo de imagen exista en: `https://github.com/piztian/Accesorios-Celucenter/tree/main/fotos`
- Verifica que el nombre en la columna N coincida exactamente con el nombre del archivo
- Si no hay imagen, aparecerá un placeholder (📦)

**P: Los favoritos se borraron**
- Los favoritos se guardan en el navegador. Si limpias el historial/caché, se perderán
- Abre el catálogo en modo incógnito para no perder favoritos

**P: No puedo editar el precio de un producto**
- Los precios vienen automáticamente de tu Google Sheet
- Edita el valor en la columna L (Lista F) del Sheet
- Los cambios se verán en el catálogo al recargar la página

---

## 📱 Compatible con

- ✅ Chrome/Edge (recomendado)
- ✅ Firefox
- ✅ Safari
- ✅ Navegadores móviles (iOS/Android)

---

## 📝 Licencia

Propiedades de CELUCENTER. Uso interno únicamente.

---

## 👤 Soporte

Para reportar problemas o sugerencias, contacta al equipo de desarrollo.

---

**Última actualización:** Febrero 2025  
**Versión:** 2.0
