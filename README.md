# Bug Slayer

> **Misión: Encontrar y eliminar todos los bugs hasta dejar cero.**

El Bug Slayer es un agente especializado que no descansa hasta que no quede
ningún bug en el proyecto indicado. Combina auditoría exhaustiva, debugging
sistemático y corrección automatizada en un flujo de trabajo iterativo.

**Core principle:** No se detiene hasta que el proyecto está limpio. Cero bugs.

---

## Información General

| Campo | Valor |
|-------|-------|
| **Nombre** | Bug Slayer |
| **Versión** | 1.2.0 |
| **Autor** | devFuentesQuijon & Hermes Agent |
| **Licencia** | MIT |
| **Skill Hermes** | `software-development/bug-slayer` |
| **Skills relacionadas** | `multi-agent-auditing`, `systematic-debugging`, `requesting-code-review`, `test-driven-development`, `plan` |
| **Plataformas soportadas** | Linux, macOS, Windows |

---

## Cuando Usar

### Usar Bug Slayer cuando...

- Se pide "eliminar bugs", "zero bugs", "limpiar bugs" o se invoca `bug-slayer`
- El usuario indica un proyecto y solicita auditoría + corrección completa
- Hubo un despliegue fallido o incidente en producción
- Se hereda un proyecto desconocido y necesita estabilización
- Hay un release importante o migración crítica próxima
- Se quiere establecer un baseline de calidad antes de entregar

### No usar Bug Slayer cuando...

- Se está desarrollando una feature nueva: usar `plan` + `test-driven-development`
- Es una revisión puntual de PR: usar `requesting-code-review`
- Es un bug aislado de debugging: usar `systematic-debugging`
- Se necesita documentación o arquitectura inicial: usar `plan`

---

## Filosofía

### El Mantra del Bug Slayer

```
NO PARA HASTA QUE NO QUEDE NINGUNO
PREPARAR → AUDITAR → ENCONTRAR → CORREGIR → VERIFICAR → REPETIR
```

### Principios Inquebrantables

1. **Cero bugs como objetivo innegociable**: No se entrega el proyecto hasta confirmar cero bugs.
2. **Read-only en auditoría**: Los agentes de auditoría solo leen código; nunca modifican archivos durante la fase de descubrimiento.
3. **Deduplicación inteligente**: Si múltiples agentes reportan el mismo bug, se consolida un solo hallazgo con la evidencia más detallada.
4. **Verificación antes de corrección**: Todo hallazgo debe ser verificado leyendo el código exacto antes de aplicar un fix.
5. **Tests de regresión obligatorios**: Cada bug crítico o alto debe tener un test que lo prevenga de recurrencia.
6. **Control de versiones primero**: Nunca auditar sin Git ni sin backup; sin rollback, no hay auditoría segura.
7. **Manual como fallback**: Si los agentes fallan 2 veces, se audita manualmente. No se insiste con re-lanzamientos indefinidos.

---

## Requisitos Previos

### Herramientas

- `git` >= 2.0
- Python 3.8+ (para scripts de verificación)
- Proyecto bajo control de versiones recomendado

### Skills Relacionadas

- `software-development/multi-agent-auditing`
- `software-development/systematic-debugging`
- `software-development/test-driven-development`
- `software-development/plan`
- `software-development/requesting-code-review`

---

## Instalación

### Opción 1: Instalar desde el release (recomendado para usuarios finales)

1. Descargar el paquete desde GitHub Releases:

```bash
curl -L -o bugslayer-v1.2.0.tar.gz \
  https://github.com/devFuentesQuijon/BugSlayer/releases/download/v1.2.0/bugslayer-v1.2.0.tar.gz
```

2. Extraer en el directorio de skills de Hermes:

```bash
mkdir -p ~/.hermes/skills/software-development
tar -xzf bugslayer-v1.2.0.tar.gz -C ~/.hermes/skills/software-development/
```

El resultado esperado es:

```text
~/.hermes/skills/software-development/bug-slayer/
├── SKILL.md
├── README.md
├── templates/
├── scripts/
└── references/
```

3. Verificar la instalación:

```bash
ls ~/.hermes/skills/software-development/bug-slayer/SKILL.md
```

### Opción 2: Clonar desde el repositorio de GitHub

```bash
git clone https://github.com/devFuentesQuijon/BugSlayer.git \
   ~/.hermes/skills/software-development/bug-slayer
```

### Opción 3: Copia desde una instalación local existente

Si ya tenés la skill en otro equipo o en este equipo, copiarla directamente:

```bash
cp -r /ruta/local/bug-slayer \
   ~/.hermes/skills/software-development/bug-slayer
```

### Verificación post-instalación

Confirmar que Hermes cargue la skill sin errores:

```bash
hermes skills list | grep bug-slayer
```

Para usarla, mencioná `bug-slayer` o ejecutala sobre un proyecto, por ejemplo:

```
Ejecuta Bug Slayer sobre /ruta/al/proyecto
```

### Actualización

Para actualizar a una nueva versión desde Releases:

```bash
mv ~/.hermes/skills/software-development/bug-slayer \
   ~/.hermes/skills/software-development/bug-slayer.bak-$(date +%Y%m%d)
curl -L -o bugslayer-v<nueva-version>.tar.gz \
   https://github.com/devFuentesQuijon/BugSlayer/releases/download/v<nueva-version>/bugslayer-v<nueva-version>.tar.gz
mkdir -p ~/.hermes/skills/software-development
tar -xzf bugslayer-v<nueva-version>.tar.gz \
   -C ~/.hermes/skills/software-development/
```

---

## Estructura de la Skill

```
software-development/bug-slayer/
├── README.md              # Esta guía
├── SKILL.md               # Definción técnica de la skill para Hermes
│
├── templates/             # Plantillas reutilizables
│   └── zero-bugs-report.md
│
├── scripts/               # Scripts auxiliares
│   └── verify-zero-bugs.py
│
├── references/            # Lecciones aprendidas y guías específicas
│   ├── audit-without-git.md
│   ├── verifying-bug-slayer-findings.md
│   ├── agent-monitoring.md
│   ├── agent-monitoring-proactive.md
│   ├── async-delegation-behavior.md
│   ├── bug-fixing-patterns.md
│   ├── bug-taxonomy-by-language.md
│   └── session-lessons-*.md
```

---

## Las 7 Fases

| Fase | Nombre | Duración | Responsable |
|------|--------|----------|-------------|
| **0** | Preparación del Proyecto | 2-5 min | Agente Padre |
| **1** | Reconocimiento | 5-15 min | Agente Padre |
| **2** | Auditoría Multi-Agente o Manual | 15-60 min | 3 Agentes / Padre |
| **3** | Espera + Verificación | 5-20 min | Agente Padre |
| **4** | Consolidación del Reporte | 5-10 min | Agente Padre |
| **5** | Exterminación de Bugs | Variable | Agente Padre + Fixes |
| **6** | Verificación de Cero Bugs | 10-30 min | Agente Padre |
| **7** | Prevención (Opcional) | Variable | Agente Padre |

### Fase 0: Preparación del Proyecto

Antes de auditar, se prepara el proyecto para una auditoría segura.

** Pasos obligatorios:**

1. Verificar control de versiones:

   ```bash
   cd <project_dir>
   git status 2>/dev/null || echo "NO HAY GIT INICIALIZADO"
   ```

2. Si NO hay Git, advertir al usuario y ofrecer inicializarlo o hacer backup:

   ```bash
   cp -r <project_dir> <project_dir>.bug-slayer-backup-$(date +%Y%m%d-%H%M%S)
   ```

3. Pre-flight check de delegación:

   ```bash
   delegate_task(
       goal="Pre-flight check: reporta 'OK' y nada más.",
       context="Este es un pre-flight check. Responde exactamente 'OK'.",
       role="leaf",
       toolsets=["terminal"]
   )
   ```

   Si después de 2-3 minutos el agente no retorna, usar **auditoría manual directa** y no re-lanzar.

### Fase 1: Reconocimiento

Escaneo rápido para entender el alcance del proyecto. Solo lo necesario para breafear agentes.

**Comandos:**

```bash
# Estructura del proyecto
find <project_dir> -type f | head -50

# Líneas de código por tipo
find <project_dir> -type f \( -name "*.py" -o -name "*.js" -o -name "*.ts" \) | xargs wc -l | tail -1

# Tests existentes
find <project_dir> -type f -name "*test*" | wc -l

# Archivos críticos
ls -la <project_dir>/{Dockerfile,docker-compose*.yml,requirements.txt,package.json,go.mod,Cargo.toml,.env*}
```

**Leer SOLO:**

- Archivos de dependencias: `requirements.txt`, `package.json`, `go.mod`, `Cargo.toml`
- Configuración crítica: `Dockerfile`, `.env.example`
- Visión general: `README.md`
- 2-3 archivos fuente más grandes para entender arquitectura

**DETENERSE AQUÍ.** No leer más archivos; los subagentes harán el trabajo detallado.

### Fase 2: Auditoría Multi-Agente o Manual

**Decisión automática:**

| Condición | Acción |
|----------------|-----------|
| Proyecto <= 2000 líneas, pre-flight OK | 3 agentes en paralelo |
| Proyecto 2000-5000 líneas, pre-flight OK | 3 agentes con monitoreo cada 5 min |
| Proyecto > 5000 líneas | Auditoría manual directa |
| Pre-flight falla o segunda falla de agentes | Auditoría manual directa |

**Agentes de auditoría (SIEMPRE read-only):**

1. **Cazador de Bugs Críticos** - seguridad, estabilidad, integridad de datos
2. **Cazador de Bugs Funcionales** - lógica, APIs, integraciones, RAG
3. **Cazador de Bugs de Calidad** - arquitectura, rendimiento, deuda técnica, observabilidad

Cada agente debe devolver hallazgos en formato estandarizado con severidad, archivo, línea, evidencia, impacto y solución sugerida.

### Fase 3: Espera + Verificación (Regla Crítica)

- Después de lanzar agentes, **NO** seguir leyendo archivos ni analizando.
- Esperar el reporte consolidado; emitir monitoreo periódico solo en proyectos >5000 líneas.
- Cuando retornan, verificar que **no modificaron archivos**:

  ```bash
  git status --short
  # Si hay cambios, revertir y re-lanzar con reglas más estrictas
  ```

- Verificar hallazgos leyendo el código exacto antes de crear TODOs.
- Clasificar: CONFIRMADO / FALSO POSITIVO / PARCIAL / YA CORREGIDO.

### Fase 4: Consolidación del Reporte

Consolidar hallazgos en reporte unificado por severidad:

```markdown
# 🐛🔥 REPORTE BUG SLAYER — Nombre del Proyecto

## Resumen Ejecutivo
- Total de bugs encontrados: X
- Críticos: X | Altos: X | Medios: X | Bajos: X

## 🔴 CRÍTICOS
| ID | Archivo | Línea | Descripción | Solución |
|----|---------|---------|-----------------|---------------|
| C1 | ... | ... | ... | ... |

## 🟠 ALTOS
## 🟡 MEDIOS
## 🟢 BAJOS
```

### Fase 5: Exterminación de Bugs

Cuando el usuario aprueba, se corrigen los bugs en orden de severidad.

**Patrón:**

1. Marcar TODO `in_progress`
2. Leer líneas exactas
3. Parchear con `patch()`
4. Verificar con tests/lint
5. Marcar TODO `completed`

**Procesar: CRÍTICO → ALTO → MEDIO → BAJO**

- Un cambio a la vez
- No parchear a ciegas
- Si `patch` falla 2 veces, releer y ajustar
- Crear test de regresión por cada bug CRÍTICO/ALTO
- Ejecutar suite completa después de cada batch de severidad

### Fase 6: Verificación de Cero Bugs

1. **Verificación estática**: re-ejecutar agentes en modo verificación o auditoría manual.
2. **Verificación dinámica**:

   ```bash
   pytest tests/ -v
   ruff check .
   mypy . --ignore-missing-imports
   pytest --cov=src --cov-report=term-missing
   ```

3. **Verificación manual**: `git diff`, ausencia de `print()` de debug, `except: pass`, comentarios temporales.
4. **Reporte final** con tabla antes/después.
5. **Si usa Docker**, verificar despliegue activo:

   ```bash
   docker ps --format "table {{.Names}}\t{{.Status}}\t{{.Ports}}"
   docker logs --tail 50 <container_name>

   docker compose -f <compose-file> build --no-cache
   docker compose -f <compose-file> up -d
   ```

### Fase 7: Prevención (Opcional)

- Pre-commit hooks: lint, tests, security scan
- CI/CD pipeline con tests automáticos
- Monitoreo y alertas en producción
- Re-ejecutar Bug Slayer periódicamente (sprint/mes)

---

## Matriz de Severidad

| Severidad | Definición | Tiempo de Respuesta | Ejemplos |
|-----------|-----------------|---------------------|----------|
| **CRÍTICO** | Caída, seguridad, pérdida de datos | Inmediato | SQL injection, deadlock en transacción, null pointer en producción |
| **ALTO** | Funcionalidad rota, rendimiento inaceptable | Esta semana | N+1 queries, algoritmo incorrecto, API erróneos |
| **MEDIO** | Edge case, deuda técnica, workaround | Este mes | Falta validación opcional, código duplicado, `except: pass` |
| **BAJO** | Mejora incremental, code smell | Backlog | Nombre poco claro, falta type hints, comentario obsoleto |

---

## Ejemplo de Flujo

```text
Usuario: "Ejecuta Bug Slayer sobre /home/david/proyecto"

Hermes:
1. Fase 0: Verifica git status → OK, backup creado
2. Fase 0: Pre-flight check → agentes funcionan
3. Fase 1: Lista estructura, LOC, tests, dependencias
4. Fase 2: Lanza 3 agentes de auditoría (read-only)
5. Fase 3: Espera resultados consolidados, verifica integridad
6. Fase 4: Consolida reporte con 8 bugs (2 críticos, 3 altos, 2 medios, 1 bajo)
7. Fase 5: Usuario aprueba → crea TODOs y corrige por severidad
8. Fase 5: Aplica fixes, crea tests de regresión, ejecuta suite
9. Fase 6: Verifica cero bugs, construye Docker, valida despliegue
10. Fase 7: Configura pre-commit hooks
11. Entregar reporte final: CERO BUGS, 8 corregidos, cobertura mejorada
```

---

## Troubleshooting

### Los agentes no retornan después del dispatch

- No asumir fallo de inmediato; `delegate_task` es asíncrono.
- Después de 2-3 minutos sin respuesta, proceder con auditoría manual directa.
- Ver `references/async-delegation-behavior.md`.

### Los agentes modifican archivos durante la auditoría

- Violación del modo read-only.
- Revertir cambios, re-lanzar con reglas más estrictas.
- Ver `references/audit-without-git.md`.

### Proyecto sin Git

- Ofrecer inicializar Git o hacer backup manual antes de auditar.
- Documentar en el reporte que no hay rollback automático.

### Proyecto muy grande (>5000 líneas)

- Usar auditoría manual directa desde Fase 2.
- No esperar a que fallen los agentes; es más confiable evitar delegación en este caso.

### Parche fallido dos veces

- Releer el archivo; el contenido cambió o el `old_string` no es correcto.
- No reintentar una tercera vez con los mismos argumentos.

---

## Lecciones Aprendidas

- `delegate_task` es asíncrono; los resultados pueden llegar como mensaje async `[ASYNC DELEGATION BATCH COMPLETE]`. No asumir fallo por `process(action='list')` vacío inmediatamente.
- Subagentes con fallos silenciosos deben reemplazarse por auditoría manual tras 2 intentos.
- Verificar siempre `git status` antes y después de cualquier operación.
- Verificar despliegues Docker activos; un repo limpio no implica un despliegue actualizado.
- Prefierir implementación manual sobre re-lanzar subagentes después de fallos previos.

Documentación detallada en archivos de `references/`.

---

## Licencia

MIT - Hermes Agent © Nous Research

## Changelog

### v1.2.0
- Reescritura completa del `SKILL.md` con flujo reordenado.
- Mitigación de fallos silenciosos: pre-flight doble, timeouts explícitos y fallback a manual.
- Auditoría manual directa clarificada como modo principal para proyectos grandes.
- Nuevo `bugslayer-methodology.md`: metodología framework-agnóstica.
- Actualización de installation guide en README.

### v1.1.0
- Publicación inicial en GitHub Releases.
- Paquete distribuible `bugslayer-v1.2.0.tar.gz`.
- README con guía de instalación desde release o repo.
