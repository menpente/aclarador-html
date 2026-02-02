# Aclarador HTML Tool

Herramienta HTML de archivo único para analizar documentos en carpetas usando principios de lenguaje claro del Manual de Estilo del Gobierno de Aragón.

## 🎯 Descripción

Esta herramienta convierte la aplicación [aclarador-clean](https://github.com/menpente/aclarador-clean) en un **HTML tool** siguiendo los patrones de [Simon Willison](https://simonwillison.net/2025/Dec/10/html-tools/):

- ✅ **Un solo archivo** - Todo el código HTML, CSS y JavaScript en un archivo
- ✅ **Sin instalación** - Simplemente abre el archivo en tu navegador
- ✅ **Procesamiento por lotes** - Analiza todas las carpetas completas
- ✅ **Privacy-first** - Los archivos se procesan localmente (solo se envía texto a la API)
- ✅ **Multi-agente** - Sistema completo con 6 agentes especializados

## 🚀 Cómo Usar

### 1. Obtener una clave API de Groq

1. Ve a [console.groq.com](https://console.groq.com)
2. Crea una cuenta o inicia sesión
3. Genera una clave API

### 2. Abrir la Herramienta

1. Descarga `aclarador-html-tool.html`
2. Ábrelo en un navegador moderno (Chrome, Edge, Firefox, Safari)

### 3. Configurar y Analizar

1. **Ingresa tu clave API** de Groq (se guarda localmente en tu navegador)
2. **Selecciona una carpeta** con documentos de texto
3. **Selecciona archivos** específicos o usa "Analizar Todos"
4. **Espera** mientras se procesan los documentos
5. **Revisa resultados** con comparaciones antes/después
6. **Descarga** versiones corregidas

## 🤖 Agentes Incluidos

La herramienta usa 6 agentes especializados:

| Agente | Función |
|--------|---------|
| **Analyzer** | Clasifica texto y detecta problemas |
| **Rewriter** | Reescritura completa usando Llama 3.3 70B |
| **Grammar** | Correcciones gramaticales |
| **Style** | Mejoras de estilo y legibilidad |
| **SEO** | Optimización para contenido web |
| **Validator** | Validación final y puntuación |

## 📋 Tipos de Archivos Soportados

- `.txt` - Archivos de texto plano
- `.md` / `.markdown` - Documentos Markdown
- `.html` / `.htm` - HTML
- `.css` - Hojas de estilo
- `.js` - JavaScript
- `.json` - JSON
- `.xml` - XML
- `.csv` - CSV
- `.log` - Logs

## 🎨 Características

### Interfaz de Usuario

- 📁 **Selector de carpetas** con File System Access API
- ✅ **Selección múltiple** de archivos
- 📊 **Barra de progreso** en tiempo real
- 🔄 **Comparación lado a lado** (original vs mejorado)
- 💾 **Descarga individual** de archivos corregidos

### Análisis

- 🔍 **Detección de problemas**:
  - Oraciones largas (>30 palabras)
  - Voz pasiva
  - Vocabulario complejo
  - Problemas gramaticales

- ✨ **Mejoras automáticas**:
  - División de oraciones
  - Conversión a voz activa
  - Simplificación de vocabulario
  - Optimización SEO (para contenido web)

### Métricas

- **Calidad**: Puntuación general (0-100%)
- **Legibilidad**: Basada en longitud de oraciones
- **Severidad**: Clasificación de problemas detectados

## 🔒 Privacidad y Seguridad

- ✅ Los archivos **nunca se suben** a ningún servidor
- ✅ Solo el **contenido de texto** se envía a la API de Groq para análisis
- ✅ La clave API se almacena **localmente** en tu navegador (localStorage)
- ✅ Todo el procesamiento ocurre **en tu navegador**

## 💡 Principios de Lenguaje Claro

La herramienta aplica los principios del Manual de Estilo del Gobierno de Aragón:

1. **Una idea por oración** - Máximo 30 palabras
2. **Voz activa** - Evitar construcciones pasivas
3. **Vocabulario común** - Palabras simples y precisas
4. **Puntuación estratégica** - Mejorar la claridad
5. **Eliminar redundancias** - Texto conciso
6. **Evitar jerga** - Lenguaje accesible

## 🛠️ Requisitos Técnicos

### Navegador

- **Chrome/Edge 86+** - Soporte completo para File System Access API
- **Firefox 111+** - Soporte experimental
- **Safari 15.2+** - Soporte parcial

### API

- Clave API de Groq (gratuita)
- Modelo usado: `llama-3.3-70b-versatile`

## 📖 Ejemplos de Uso

### Caso 1: Documentación Técnica

```
Original: "La implementación de la metodología requiere la utilización
de infraestructura tecnológica subyacente y paradigmas operacionales
que están siendo utilizados dentro del marco organizacional."

Mejorado: "Para aplicar este método necesitas usar la tecnología
disponible. También debes seguir los procesos de tu organización."
```

### Caso 2: Contenido Web

```
Original: "El servicio que ha sido proporcionado por el departamento
fue diseñado con el objetivo de maximizar la satisfacción del usuario."

Mejorado: "El departamento diseñó este servicio para satisfacer mejor
a los usuarios."
```

## 🔧 Personalización

El archivo es completamente modificable:

- **Estilos CSS**: Líneas 7-400 (aproximadamente)
- **Agentes**: Líneas 500-900 (aproximadamente)
- **UI**: Líneas 950-1200 (aproximadamente)

Puedes ajustar:
- Colores y temas
- Límites de longitud de oraciones
- Prompts de los agentes
- Tipos de archivos soportados

## 📚 Recursos

- [Aclarador Clean (original)](https://github.com/menpente/aclarador-clean)
- [Simon Willison - HTML Tools](https://simonwillison.net/2025/Dec/10/html-tools/)
- [Groq API Documentation](https://console.groq.com/docs)
- [File System Access API](https://developer.mozilla.org/en-US/docs/Web/API/File_System_Access_API)

## 🐛 Solución de Problemas

### "Tu navegador no soporta la selección de carpetas"

- Usa Chrome, Edge, o un navegador moderno
- Actualiza tu navegador a la última versión

### "API error: 401"

- Verifica que tu clave API sea correcta
- Asegúrate de que la clave no haya expirado

### "API error: 429"

- Has excedido el límite de tasa de la API
- Espera unos minutos antes de continuar
- Considera actualizar tu plan de Groq

### Los resultados no se muestran

- Abre la consola del navegador (F12)
- Revisa si hay errores
- Verifica tu conexión a internet

## 📝 Licencia

Este proyecto se deriva de [aclarador-clean](https://github.com/menpente/aclarador-clean).

## 🤝 Contribuciones

¿Mejoras o sugerencias? Abre un issue o pull request en el repositorio.

---

**Creado como HTML tool siguiendo los patrones de Simon Willison**
