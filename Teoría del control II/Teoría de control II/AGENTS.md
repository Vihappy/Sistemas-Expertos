# AGENTS.md — Esquema de la Ontología de Teoría de Control II

Este documento es el **esquema maestro** de la wiki. Define la ontología, las convenciones de páginas y los flujos de trabajo que debes seguir para mantener la base de conocimiento. Es el archivo de configuración más importante del proyecto.

---

## 1. Propósito de la wiki

Construir una **ontología persistente y acumulativa** de Teoría de Control II, organizada en páginas de Markdown interconectadas. La wiki es el "códigobase": el LLM lee fuentes brutas (`raw/`), extrae conocimiento y lo integra en páginas de wiki (`wiki/`), manteniendo consistencia, referencias cruzadas y un log de evolución.

**Principio rector:** El conocimiento se compila una vez y se mantiene vigente. No se rediscovered desde cero en cada consulta.

---

## 2. Arquitectura de tres capas

```
Teoría de control II/
├── llm-wiki.md          # Documento original (leído, nunca modificado)
├── AGENTS.md            # Este esquema (leído, nunca modificado salvo consenso)
├── raw/                 # Fuentes brutas (inmutables)
│   ├── assets/          # Imágenes descargadas localmente
│   └── sources/         # Documentos fuente crudos
├── wiki/                # Página generadas y mantenidas por el LLM
│   ├── index.md         # Catálogo contenido-contenido
│   ├── log.md           # Registro cronológico append-only
│   ├── 00-overview.md   # Vista general de la ontología
│   ├── concepts/        # Páginas de conceptos y entidades
│   ├── methods/         # Páginas de métodos y técnicas
│   └── sources/         # Resúmenes de fuentes ingeridas
└── .obsidian/           # Configuración de Obsidian (no tocar)
```

---

## 3. Ontología del dominio (Teoría de Control II)

La ontología se organiza en **5 dominios principales**. Cada página de wiki representa una entidad o concepto de la ontología.

### 3.1 Dominio A: Fundamentos
Conceptos básicos que definen el lenguaje de la disciplina.

| Concepto | Tipo | Definición breve |
|----------|------|------------------|
| Sistema de control | Entidad | Conjunto de componentes que dirige el comportamiento de otro sistema |
| Planta | Entidad | El sistema físico o proceso que se desea controlar |
| Controlador | Entidad | Dispositivo o algoritmo que calcula la acción de control |
| Señal de entrada | Entidad | Referencia o comando aplicado al sistema |
| Señal de salida | Entidad | Respuesta medida del sistema |
| Perturbación | Entidad | Entrada no deseada que afecta al sistema |
| Error de control | Entidad | Diferencia entre referencia y salida |
| Realimentación | Concepto | Proceso de medir la salida y usarla para corregir la entrada |
| Lazo abierto | Concepto | Control sin medir la salida |
| Lazo cerrado | Concepto | Control con realimentación de la salida |

### 3.2 Dominio B: Modelado Matemático
Representación formal de los sistemas.

| Concepto | Tipo | Definición breve |
|----------|------|------------------|
| Función de transferencia | Concepto | Relación entrada-salida en el dominio de Laplace |
| Espacio de estados | Concepto | Representación por variables de estado |
| Ecuaciones diferenciales | Concepto | Modelo dinámico en el tiempo |
| Linealización | Concepto | Aproximación lineal de un sistema no lineal |
| Diagrama de bloques | Concepto | Representación gráfica de señales y operaciones |
| Grafo de flujo de señales | Concepto | Representación por nodos y ramas (regla de Mason) |
| Polos | Concepto | Raíces del denominador de la función de transferencia |
| Ceros | Concepto | Raíces del numerador de la función de transferencia |
| Ganancia | Concepto | Factor de amplificación de una señal |

### 3.3 Dominio C: Análisis de Sistemas
Estudio del comportamiento de los sistemas.

| Concepto | Tipo | Definición breve |
|----------|------|------------------|
| Estabilidad | Concepto | Capacidad de retornar al equilibrio tras una perturbación |
| Controlabilidad | Concepto | Capacidad de llevar el sistema a cualquier estado |
| Observabilidad | Concepto | Capacidad de inferir el estado interno desde la salida |
| Respuesta temporal | Concepto | Comportamiento del sistema en el dominio del tiempo |
| Respuesta en frecuencia | Concepto | Comportamiento frente a entradas sinusoidales |
| Error en estado estacionario | Concepto | Error residual cuando el sistema se estabiliza |
| Margen de ganancia | Concepto | Factor adicional de ganancia para llegar a la inestabilidad |
| Margen de fase | Concepto | Retraso de fase adicional para llegar a la inestabilidad |

### 3.4 Dominio D: Diseño de Controladores
Técnicas para lograr un comportamiento deseado.

| Concepto | Tipo | Definición breve |
|----------|------|------------------|
| Control PID | Método | Controlador proporcional-integral-derivativo |
| Compensación en adelanto | Método | Añade fase para mejorar estabilidad y respuesta |
| Compensación en atraso | Método | Aumenta ganancia baja frecuencia reduciendo error |
| Realimentación de estados | Método | Usa variables de estado para calcular la entrada |
| Asignación de polos | Método | Coloca polos del sistema en lazo cerrado |
| Observador de estados | Método | Estima variables de estado no medidas |
| Control óptimo LQR | Método | Minimiza un índice de costo cuadrático |

### 3.5 Dominio E: Métodos Avanzados
Extensiones de la teoría básica.

| Concepto | Tipo | Definición breve |
|----------|------|------------------|
| Control robusto | Método | Diseña tolerante a incertidumbre del modelo |
| Control adaptativo | Método | Ajusta parámetros en línea para sistemas variables |
| Control digital | Método | Implementa control en sistemas discretos |
| Control no lineal | Método | Trata sistemas que no obedecen superposición |
| Control robusto H∞ | Método | Minimiza la ganancia de pico del sistema |
| Control adaptativo MRAC | Método | Ajuste basado en referencia de modelo |

---

## 4. Relaciones ontológicas (propiedades)

Cada página debe declarar sus relaciones con otras usando estas propiedades:

| Propiedad | Rango | Dominio | Descripción |
|-----------|-------|---------|-------------|
| `es-un` | Concepto | Concepto | Subtipo o clasificación de otro concepto |
| `modela` | Entidad | Concepto | Una entidad usa una representación/modelo |
| `analiza` | Método | Concepto | Un método analiza una propiedad |
| `diseña` | Método | Entidad | Un método diseña un controlador |
| `depende-de` | Concepto | Concepto | Un concepto requiere otro para definirse |
| `contrasta-con` | Concepto | Concepto | Dos conceptos son mutuamente excluyentes o opuestos |
| `se-mide-con` | Concepto | Método | Un concepto se cuantifica mediante un método |
| `aparece-en` | Concepto | Concepto | Un concepto surge en el contexto de otro |
| `ejemplo-de` | Entidad | Concepto | Una instancia concreta de un concepto |

**Ejemplo:** `lugar-de-las-raices.md` tiene `analiza: estabilidad` y `se-mide-con: margen-de-fase`.

---

## 5. Convenciones de páginas

### 5.1 Formato de archivo
- Archivo: `wiki/concepts/nombre-del-concepto.md` o `wiki/methods/nombre-del-metodo.md`
- Nombre en español, en minúsculas, separado por guiones bajos
- Extensión `.md`

### 5.2 Frontmatter obligatorio (YAML)
```yaml
---
tipo: concepto
dominio: modelado
tags: [control, modelado]
fecha-creacion: 2026-09-19
estado: estable
---
```

**Valores permitidos para `tipo`:** `concepto`, `entidad`, `metodo`, `metrica`, `fuente`
**Valores permitidos para `estado`:** `borrador`, `en-validacion`, `estable`, `contradicho`

### 5.3 Estructura interna de página
```markdown
# Nombre del Concepto

> Resumen en 1-2 frases. ¿Qué es y por qué importa?

## Definición formal
Texto preciso con notación matemática cuando corresponda.

## Relaciones ontológicas
- es-un: [[Concepto padre]]
- modela: [[Modelo]]
- depende-de: [[Concepto dependiente]]

## Ecuaciones clave
```latex
Ecuación importante
```

## Interpretación física
Explicación intuitiva de lo que representa.

## Ejemplos
- Ejemplo concreto aplicado

## Fuentes
- [[Resumen de fuente]]

## Preguntas abiertas
- ¿Qué falta por aclarar?
```

---

## 6. Flujos de trabajo

### 6.1 Ingest (ingerir una fuente)
Cuando agregas una fuente a `raw/sources/`:
1. Lee la fuente completa
2. Discute los hallazgos clave con el usuario (si aplica)
3. Crea una página de resumen en `wiki/sources/`
4. Actualiza `wiki/index.md`
5. Actualiza páginas relevantes en `wiki/concepts/` y `wiki/methods/`
6. Añade una entrada al `wiki/log.md` con el prefijo `## [YYYY-MM-DD] ingest`

### 6.2 Query (consultar)
Cuando respondes una pregunta:
1. Lee `wiki/index.md` primero
2. Busca páginas relevantes en `wiki/concepts/` y `wiki/methods/`
3. Sintetiza la respuesta con citas a páginas (`[[nombre]]`)
4. Si la respuesta es valiosa, archívala como nueva página en la wiki

### 6.3 Lint (mantenimiento periódico)
Ejecuta un health-check regularmente buscando:
- Contradicciones entre páginas
- Reclamos obsoletos por fuentes nuevas
- Páginas huérfanas sin enlaces entrantes
- Conceptos importantes sin página propia
- Referencias cruzadas faltantes
- Brechas de datos que requieran búsqueda web

---

## 7. Convenciones de index y log

### 7.1 `wiki/index.md`
Catálogo contenido-contenido. Cada entrada:
```markdown
- [[nombre-de-pagina]] — resumen de una línea
```
Organizado por dominio (A, B, C, D, E).

### 7.2 `wiki/log.md`
Registro cronológico append-only. Formato:
```markdown
## [2026-09-19] ingest | Nombre de la fuente
- Acciones realizadas: ...
```

---

## 8. Reglas de calidad

1. **Consistencia terminológica:** usar siempre el mismo término español en todas las páginas.
2. **Notación matemática:** usar LaTeX para ecuaciones (`$$ ... $$` o `\(...\)`).
3. **Referencias cruzadas:** toda página debe enlazar al menos 2 páginas relacionadas.
4. **Trazabilidad:** cada afirmación derivada de una fuente debe citar la página de resumen en `wiki/sources/`.
5. **Estado de validación:** páginas sin fuente verificable deben marcarse como `borrador`.
6. **No modificar raw:** las fuentes en `raw/` son inmutables; nunca se editan.

---

## 9. Nota de co-evolución

Este esquema es vivo. A medida que la ontología crece, se pueden añadir dominios, propiedades o convenciones. Cualquier cambio debe registrarse en `wiki/log.md` y discutirse con el usuario.
