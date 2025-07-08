# Plantilla de Ingeniería de Contexto

Una plantilla completa para empezar con la Ingeniería de Contexto, la disciplina de diseñar contexto para asistentes de codificación de IA para que tengan toda la información necesaria para realizar tareas de principio a fin.

> **La Ingeniería de Contexto supera a la ingeniería de prompts por un orden de magnitud, y ofrece mucha más estructura y fiabilidad que la codificación por intuición. Esta plantilla está optimizada para su uso con Gemini CLI.**

## 🚀 Inicio Rápido

```bash
# 1. Clona esta plantilla
git clone https://github.com/coleam00/Context-Engineering-Intro.git
cd Context-Engineering-Intro

# 2. Instala y autentica Gemini CLI
npm install -g @google/gemini-cli
gemini auth

# 3. Configura las reglas de tu proyecto (opcional - se proporciona plantilla)
# Edita GEMINI.md para añadir tus directrices específicas del proyecto

# 4. Añade ejemplos (muy recomendado)
# Coloca ejemplos de código relevantes en la carpeta `examples/`

# 5. Crea tu solicitud de funcionalidad inicial
# Edita INITIAL.md con los requisitos de tu funcionalidad

# 6. Genera un PRP (Prompt de Requisitos de Producto) completo
gemini -p "@./.gemini/commands/generate-prp.md" "INITIAL.md"

# 7. Ejecuta el PRP para implementar tu funcionalidad
gemini -p "@./.gemini/commands/execute-prp.md" "PRPs/your-feature-name.md"
````

## 📚 Tabla de Contenidos

* [¿Qué es la Ingeniería de Contexto?](#qué-es-la-ingeniería-de-contexto)
* [Estructura de la Plantilla](#estructura-de-la-plantilla)
* [Guía Paso a Paso](#guía-paso-a-paso)
* [Cómo Escribir Archivos INITIAL.md Efectivos](#cómo-escribir-archivos-initialmd-efectivos)
* [El Flujo de Trabajo PRP](#el-flujo-de-trabajo-prp)
* [Uso Efectivo de Ejemplos](#uso-efectivo-de-ejemplos)
* [Mejores Prácticas](#mejores-prácticas)
* [Errores Comunes](#errores-comunes)
* [Recursos](#recursos)

## ¿Qué es la Ingeniería de Contexto?

La Ingeniería de Contexto representa un cambio de paradigma respecto a la ingeniería de prompts tradicional:

### Ingeniería de Prompts vs. Ingeniería de Contexto

**Ingeniería de Prompts:**

* Se enfoca en redactar instrucciones ingeniosas
* Se limita a cómo formulas la tarea
* Es como dejar una nota adhesiva

**Ingeniería de Contexto:**

* Es un sistema completo que proporciona contexto exhaustivo
* Incluye documentación, ejemplos, reglas, patrones y validación
* Es como escribir un guion completo con todos los detalles

### ¿Por Qué es Importante la Ingeniería de Contexto?

1. **Reduce los fallos de la IA**: La mayoría de errores no son del modelo, sino por falta de contexto.
2. **Asegura consistencia**: La IA respeta patrones y convenciones del proyecto.
3. **Permite funcionalidades complejas**: Puede manejar implementaciones multietapa con el contexto adecuado.
4. **Es autocorrectiva**: Los bucles de validación permiten que la IA corrija sus propios errores.

## Estructura de la Plantilla

```text
context-engineering-intro/
├── .gemini/
│   ├── commands/
│   │   ├── generate-prp.md         # Genera PRPs completos
│   │   └── execute-prp.md          # Ejecuta PRPs para implementar funcionalidades
│   └── settings.local.json         # Permisos de Gemini CLI
├── PRPs/
│   ├── templates/
│   │   └── prp_base.md             # Plantilla base para PRPs
│   └── EXAMPLE_multi_agent_prp.md  # Ejemplo de un PRP completo
├── examples/                       # Tus ejemplos de código (¡críticos!)
├── GEMINI.md                       # Reglas globales para el asistente de IA
├── INITIAL.md                      # Plantilla para solicitudes de funcionalidad
├── INITIAL_EXAMPLE.md              # Ejemplo de solicitud de funcionalidad
└── README.md                       # Este archivo
```

Próximamente se incluirán plantillas adicionales con soporte para arquitecturas basadas en RAG.

## Guía Paso a Paso

### 1. Configura las Reglas Globales (GEMINI.md)

El archivo `GEMINI.md` contiene reglas globales que el asistente de IA seguirá. Incluye:

* **Conciencia del proyecto**
* **Estructura de código**
* **Requisitos de testing**
* **Convenciones de estilo**
* **Estándares de documentación**

Puedes usar la plantilla tal cual o adaptarla a tu proyecto.

### 2. Crea tu Solicitud de Funcionalidad Inicial

Edita `INITIAL.md` con esta estructura:

```markdown
## FUNCIONALIDAD:
[Describe lo que quieres construir - sé específico con los requisitos]

## EJEMPLOS:
[Listado de archivos en `examples/` y cómo deben usarse]

## DOCUMENTACIÓN:
[Enlaces a documentación, APIs o recursos MCP]

## OTRAS CONSIDERACIONES:
[Detalles importantes que la IA no debe pasar por alto]
```

Consulta `INITIAL_EXAMPLE.md` para un ejemplo completo.

### 3. Genera el PRP

Los PRPs (Prompt de Requisitos de Producto) son planes detallados que incluyen:

* Contexto completo
* Pasos de implementación validados
* Manejo de errores
* Requisitos de pruebas

Comparación rápida:

| PRD (Documento de Requisitos de Producto) | PRP (Prompt de Requisitos de Producto)       |
| ----------------------------------------- | -------------------------------------------- |
| Redactado para humanos                    | Redactado para asistentes de codificación IA |
| Puede ser ambiguo                         | Requiere precisión y validación              |
| Más descriptivo                           | Más operativo y orientado a ejecución        |

```bash
gemini -p "@./.gemini/commands/generate-prp.md" "INITIAL.md"
```

### 4. Ejecuta el PRP

```bash
gemini -p "@./.gemini/commands/execute-prp.md" "PRPs/your-feature-name.md"
```

La IA hará lo siguiente:

1. Leer el contexto del PRP
2. Crear un plan detallado
3. Ejecutar paso a paso con validación
4. Lanzar pruebas y corregir errores
5. Verificar que todo esté correcto

## Cómo Escribir Archivos INITIAL.md Efectivos

Para una comparación más amplia entre requisitos humanos e IA, consulta la [comparación PRD vs PRP](#3-genera-el-prp).

### Secciones Clave

**FUNCIONALIDAD**

* ❌ "Crear un scraper web"
* ✅ "Crear un scraper web asíncrono con BeautifulSoup que extraiga productos, maneje rate limiting y guarde en PostgreSQL"

**EJEMPLOS**

* Usa `examples/` como referencia
* Explica qué partes deben imitarse

**DOCUMENTACIÓN**

* Incluye APIs, documentación oficial, esquemas DB

**OTRAS CONSIDERACIONES**

* Autenticación, límites de uso, errores comunes, rendimiento

## El Flujo de Trabajo PRP

### Cómo funciona `/generate-prp`

1. **Investigación**
2. **Recopilación de documentación**
3. **Creación del plan**
4. **Control de calidad**

### Cómo funciona `/execute-prp`

1. Cargar contexto
2. Planificar tareas
3. Ejecutar componentes
4. Validar y testear
5. Iterar sobre errores
6. Confirmar éxito

Consulta `EXAMPLE_multi_agent_prp.md` para un ejemplo completo.

## Uso Efectivo de Ejemplos

La carpeta `examples/` es crítica.

### Qué Incluir

1. **Patrones de estructura**
2. **Patrones de prueba**
3. **Patrones de integración**
4. **Patrones CLI**

```text
examples/
├── README.md
├── cli.py
├── agent/
│   ├── agent.py
│   ├── tools.py
│   └── providers.py
└── tests/
    ├── test_agent.py
    └── conftest.py
```

## Mejores Prácticas

### 1. Sé explícito en INITIAL.md

### 2. Proporciona ejemplos completos

### 3. Usa validaciones

### 4. Sácale partido a la documentación

### 5. Personaliza GEMINI.md

## Errores Comunes

Evita estos errores para aprovechar al máximo la Ingeniería de Contexto:

* **No usar ejemplos**: Sin patrones, la IA improvisa.
* **Descripciones vagas**: Sé específico en `INITIAL.md`.
* **Ignorar GEMINI.md**: Pierdes consistencia.
* **Sin validaciones**: El código puede quedar roto.

## Recursos

* [Documentación de Gemini CLI](https://github.com/google/gemini-cli)
* [Mejores Prácticas de Ingeniería de Contexto](https://www.philschmid.de/context-engineering)

---

**Empieza a diseñar tu contexto hoy—y desbloquea todo el potencial del desarrollo asistido por IA.**
