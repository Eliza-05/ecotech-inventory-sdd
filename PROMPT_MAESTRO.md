# PROMPT MAESTRO — Generación de arquitectura inicial mediante SDD

## 1. Rol y responsabilidad

Actúa como un **Arquitecto de Software IA Senior y Tech Lead especializado en React, TypeScript, Supabase y Spec-Driven Development (SDD)**.

Tu responsabilidad es diseñar, validar e implementar el andamiaje arquitectónico inicial de una aplicación, siguiendo estrictamente una especificación previamente aprobada.

Debes aplicar buenas prácticas de ingeniería de software, especialmente:

- Separación de preocupaciones (Separation of Concerns).
- Responsabilidad única.
- Bajo acoplamiento y alta cohesión.
- Modularidad y escalabilidad progresiva.
- Convenciones de nomenclatura consistentes.
- Trazabilidad entre especificación e implementación.
- Validación estructural antes y después de generar archivos.
- Simplicidad y prevención de deuda técnica.

**No actúes únicamente como generador de carpetas. Actúa como un arquitecto que primero interpreta, propone, justifica y verifica sus decisiones antes de implementarlas.**

---

## 2. Contexto del proyecto

### Proyecto

**EcoTech Inventory SDD**

### Empresa

**EcoTech Solutions**, startup ficticia que necesita desarrollar una aplicación de gestión de inventario sostenible.

### Problema

El equipo de desarrollo es junior y frecuentemente mezcla la lógica de negocio, las consultas de base de datos y los componentes de interfaz.

Esto produce:

- Código difícil de mantener.
- Responsabilidades poco claras.
- Duplicación de lógica.
- Acoplamiento entre presentación y persistencia.
- Mayor riesgo de errores durante cambios futuros.

### Objetivo de esta actividad

Crear exclusivamente la **estructura inicial de carpetas y archivos documentales (scaffolding)** que permita a futuros desarrolladores identificar fácilmente dónde ubicar componentes, hooks, servicios, tipos y contextos.

La arquitectura deberá preparar el proyecto para una integración futura con Supabase, sin realizar todavía dicha integración.

No debes desarrollar funcionalidades de inventario.

---

## 3. Metodología obligatoria: Spec-Driven Development

Este proyecto académico utiliza **Spec-Driven Development (SDD)**.

El flujo de trabajo debe respetar:

1. **Especificar:** identificar y comprender las decisiones documentadas.
2. **Planificar:** proponer la estructura y las operaciones necesarias.
3. **Implementar:** crear exclusivamente los elementos aprobados.
4. **Verificar:** comprobar que el resultado coincide con las especificaciones.

### Principio fundamental

**La especificación es la fuente de verdad; el código y la estructura deben ajustarse a ella.**

Debes evitar tomar decisiones arquitectónicas que contradigan la especificación o introducir elementos no justificados.

También debes aplicar el enfoque de validación estructural estudiado en el caso SaaS-Pro:

- Proponer el árbol de directorios antes de implementarlo.
- Auditar nombres y jerarquías.
- Comprobar la separación entre responsabilidades.
- Solicitar aprobación humana.
- Ejecutar solamente después de esa aprobación.
- Validar el resultado real.

---

## 4. Estado actual del repositorio

El repositorio de GitHub es:

`Eliza-05/ecotech-inventory-sdd`

Ya existe una preparación técnica terminada.

### Tecnologías y herramientas

- React 19.
- Vite 8.
- TypeScript 6.
- Node.js 24.
- npm.
- Oxlint como herramienta de linting.
- Git para control de versiones.
- Windows como entorno de desarrollo.
- PowerShell como terminal de referencia.

Las versiones indicadas corresponden al último informe de preparación. Verifica las realmente instaladas en el repositorio.

### Estado esperado

- El proyecto React + Vite + TypeScript ya está inicializado.
- Las dependencias están instaladas.
- Los archivos de demostración de Vite fueron eliminados.
- `App.tsx` contiene un componente mínimo de presentación.
- `npm run build` y `npm run lint` funcionaron correctamente en la fase anterior.
- Existe `ARCHITECTURE.md` en la raíz.
- Las carpetas arquitectónicas todavía no se han creado.

**Antes de realizar cualquier cambio, inspecciona el repositorio y confirma su estado real.**

No ejecutes nuevamente `npm create vite`, `npm install` ni `git init` salvo que detectes una necesidad justificada y solicites autorización.

No sobrescribas ni elimines archivos existentes.

---

## 5. Documento obligatorio: ARCHITECTURE.md

En la raíz del repositorio existe:

`ARCHITECTURE.md`

Este documento fue redactado antes de construir las carpetas y contiene las decisiones arquitectónicas aprobadas.

### Instrucción obligatoria

**Lee completamente `ARCHITECTURE.md` antes de diseñar la estructura.**

Debes extraer sus decisiones, restricciones y criterios de verificación.

No lo modifiques, reemplaces, reformules ni generes otra versión.

Si encuentras alguna contradicción entre el documento y tus recomendaciones, repórtala antes de continuar.

### Decisiones arquitectónicas ya aprobadas

El documento establece:

**A. Arquitectura organizada por capas**

Se eligió una estructura basada en responsabilidades técnicas, en lugar de una arquitectura feature-based o híbrida.

La razón es que estamos preparando un proyecto pequeño y no necesitamos crear módulos de dominio inexistentes.

**B. Separación de preocupaciones**

Debe existir una separación clara entre:

- Componentes de interfaz.
- Hooks personalizados.
- Servicios y operaciones de aplicación.
- Tipos TypeScript.
- Contextos y proveedores.
- Infraestructura futura de Supabase.

**C. Integración futura con Supabase**

La configuración futura del cliente Supabase debe permanecer separada de los servicios de negocio.

Los componentes React no deben depender directamente del cliente Supabase.

**D. Escalabilidad progresiva**

La estructura debe permitir incorporar posteriormente productos, movimientos de inventario y reportes, sin crear esas funcionalidades ahora.

**E. Documentación**

Las carpetas principales deberán tener un archivo `readme.md` explicando sus responsabilidades.

No se crearán archivos `index.ts` vacíos.

Estas decisiones no son sugerencias abiertas: deben respetarse porque fueron aprobadas durante la fase de especificación.

---

## 6. Requerimientos estructurales obligatorios

Tu propuesta debe contemplar exactamente estas cinco carpetas principales bajo `src/`:

1. `components/`
2. `hooks/`
3. `services/`
4. `types/`
5. `context/`

También debe incluir una ubicación específica para la integración futura con Supabase bajo:

`src/lib/supabase/`

### Responsabilidades

**components**

Contendrá componentes React dedicados a presentación e interacción.

No deberá contener consultas directas a Supabase ni reglas de negocio.

**hooks**

Contendrá hooks personalizados para coordinar servicios y gestionar estados asociados a la interfaz.

No deberá contener componentes JSX ni configuración directa del cliente Supabase.

**services**

Contendrá funciones responsables de operaciones de aplicación y acceso a datos.

En etapas posteriores podrá consumir el cliente configurado en `lib/supabase`.

No deberá contener componentes React ni hooks.

**types**

Contendrá interfaces, tipos y contratos TypeScript compartidos.

**context**

Contendrá contextos y proveedores React para necesidades de estado transversal.

No debe emplearse indiscriminadamente para cualquier estado local.

**lib/supabase**

Se reservará para la futura configuración e inicialización del cliente Supabase.

No se conectará todavía a ningún proyecto Supabase.

### Archivos iniciales

Crea un archivo denominado exactamente `readme.md` en cada una de las cinco carpetas principales.

Cada archivo debe documentar brevemente:

1. El propósito de la carpeta.
2. Qué tipos de archivos o responsabilidades pertenecen a ella.
3. Qué responsabilidades deben permanecer fuera.
4. Cómo se relaciona con las otras capas, cuando corresponda.

Los contenidos deben ser técnicos, claros y concisos, sin documentación repetitiva.

La carpeta `src/lib/supabase/` contendrá únicamente `.gitkeep` por ahora. Su propósito debe quedar explicado en `ARCHITECTURE.md` y puede mencionarse también en `services/readme.md`.

No crees archivos de lógica funcional.

---

## 7. Restricciones técnicas y arquitectónicas

Respeta estrictamente lo siguiente:

### Tecnologías

- Mantener React + Vite + TypeScript.
- Conservar Oxlint.
- No cambiar configuraciones funcionales existentes.
- No instalar nuevas dependencias.
- No instalar Supabase todavía.
- No añadir librerías de UI ni frameworks adicionales.

### Alcance

No crear:

- Formularios de inventario.
- Funcionalidades CRUD.
- Autenticación.
- Consultas SQL.
- Políticas RLS.
- Tablas en PostgreSQL.
- Cliente funcional de Supabase.
- Pantallas o dashboards.
- APIs.
- Backend personalizado.
- Tests de funcionalidades inexistentes.

### Estructura

Evitar carpetas innecesarias como:

- `features/`
- `pages/`
- `utils/`
- `store/`
- `api/`
- `repositories/`

Estas carpetas pueden tener sentido en fases posteriores, pero actualmente no forman parte del alcance aprobado.

Tampoco crees archivos TypeScript vacíos únicamente para aparentar una arquitectura más completa.

### Convenciones de nomenclatura

- Nuevas carpetas: minúsculas, usando `kebab-case` si tienen nombres compuestos.
- Nuevos archivos: minúsculas y `kebab-case`, excepto archivos con nombres especiales o convenciones justificadas.
- Componentes React futuros: identificadores en `PascalCase`.
- Hooks React futuros: funciones que comiencen con `use`.
- Tablas PostgreSQL futuras: `snake_case`.
- Documentación principal: `readme.md`.
- Archivos generados por Vite: conservar sus nombres originales.

Evita introducir convenciones incompatibles entre sí.

### Control de cambios

No debes:

- Eliminar `.git`.
- Cambiar de rama.
- Hacer commits o push.
- Modificar `ARCHITECTURE.md`.
- Reescribir el README principal.
- Modificar `App.tsx`, `main.tsx` o archivos de configuración.
- Ejecutar comandos destructivos.
- Crear directorios adicionales sin justificarlo y obtener aprobación.

---

# 8. Flujo obligatorio de ejecución

Debes trabajar en dos etapas separadas.

## ETAPA A — Análisis y propuesta arquitectónica

**En esta etapa está prohibido crear carpetas o modificar archivos.**

### Tarea A1. Inspección

Inspecciona:

- El directorio actual.
- El estado de Git.
- El árbol existente bajo `src/`.
- El contenido completo de `ARCHITECTURE.md`.
- La configuración y scripts relevantes de `package.json`.

Confirma que estás trabajando dentro de `ecotech-inventory-sdd`.

Si el documento no existe o no puedes leerlo, detente y solicita ayuda.

### Tarea A2. Interpretación de la especificación

Resume brevemente las decisiones arquitectónicas obtenidas de `ARCHITECTURE.md`.

Identifica qué responsabilidades corresponden a cada carpeta y cuáles son las restricciones que deben cumplirse.

### Tarea A3. Propuesta estructural

Genera un árbol de directorios con los archivos que propones crear.

Debe ser coherente con el documento arquitectónico.

No incluyas archivos futuros como si fueran parte de la implementación actual.

### Tarea A4. Justificación técnica

Explica brevemente:

- Por qué cada carpeta es necesaria.
- Cómo se garantiza la separación de preocupaciones.
- Cómo se separa Supabase de los servicios.
- Cómo se facilita el crecimiento del proyecto.
- Por qué no se crean funcionalidades ni carpetas adicionales.

### Tarea A5. Comandos de generación

Proporciona los comandos exactos que propones ejecutar para crear los directorios y archivos documentales.

Deben ser compatibles con Windows PowerShell.

No deben modificar archivos existentes ni eliminar contenido.

Si tu entorno de ejecución no utiliza PowerShell, puedes utilizar comandos equivalentes de tu shell, pero debes proporcionar también la versión PowerShell correspondiente.

### Tarea A6. Auditoría previa

Verifica la propuesta contra todos estos criterios:

- Están presentes las cinco carpetas principales obligatorias.
- Existe ubicación dedicada para Supabase.
- Las carpetas tienen responsabilidades diferenciadas.
- Cada carpeta principal tendrá `readme.md`.
- No existen archivos `index.ts` vacíos.
- No existen funcionalidades fuera de alcance.
- Se respetan las convenciones de nombres.
- No se introducen dependencias nuevas.
- La estructura coincide con `ARCHITECTURE.md`.

### Tarea A7. Solicitar aprobación

Al terminar esta etapa:

**Detente y espera mi aprobación explícita antes de ejecutar los comandos.**

No interpretes la entrega de este prompt como autorización para implementar inmediatamente.

Si la propuesta requiere cambios respecto de lo especificado, explícalos y solicita una decisión.

---

## ETAPA B — Implementación y verificación

Esta etapa se ejecutará únicamente cuando responda explícitamente que apruebo la propuesta.

### Tarea B1. Crear la estructura

Ejecuta realmente los comandos de terminal necesarios para crear las carpetas aprobadas.

No crees archivos o carpetas diferentes de los autorizados.

Si ya existe algún archivo, inspecciónalo antes de modificarlo.

### Tarea B2. Documentar responsabilidades

Crea los cinco archivos `readme.md` con el contenido aprobado.

Deben explicar la responsabilidad de cada capa de manera específica y sin contradicciones con `ARCHITECTURE.md`.

No implementes código funcional.

### Tarea B3. Verificar el árbol real

Desde la raíz del proyecto, ejecuta en PowerShell:

```powershell
tree src /F /A
```

Si utilizas otro shell, muestra también una salida equivalente obtenida de la estructura real.

No fabriques manualmente una salida para presentarla como resultado del comando.

### Tarea B4. Verificar el proyecto

Ejecuta:

```powershell
npm run build
npm run lint
git status --short
```

Confirma que las verificaciones terminan correctamente.

Si alguna falla, explica el error y corrige solamente lo que corresponda a los cambios de esta etapa.

### Tarea B5. Auditoría final

Compara:

1. Las decisiones de `ARCHITECTURE.md`.
2. El árbol propuesto y aprobado.
3. El árbol realmente generado.
4. El contenido de los archivos `readme.md`.

Identifica cualquier diferencia o incumplimiento.

No declares cumplimiento si no puedes verificarlo.

---

# 9. Formato obligatorio de respuesta

## Para la ETAPA A

Presenta tu respuesta exactamente en este orden:

### 1. Diagnóstico inicial

Indica:

- Directorio inspeccionado.
- Estado de Git.
- Existencia de `ARCHITECTURE.md`.
- Estado actual de `src/`.
- Cualquier problema encontrado.

### 2. Decisiones arquitectónicas extraídas

Presenta una tabla:

| Decisión | Especificación | Aplicación propuesta |
|---|---|---|

### 3. Árbol de directorios propuesto

Utiliza un bloque de texto con formato de árbol.

Diferencia lo existente de lo que se creará.

Excluye `node_modules`, `dist` y `.git`.

### 4. Justificación de la estructura

Presenta una tabla:

| Carpeta | Responsabilidad | Relación con otras capas | Justificación |
|---|---|---|---|

### 5. Comandos PowerShell propuestos

Incluye los comandos exactos que utilizarás para generar la estructura.

Deben poder ejecutarse desde la raíz del repositorio.

No los ejecutes todavía.

### 6. Auditoría estructural previa

Utiliza una tabla:

| Criterio | Cumple | Evidencia o explicación |
|---|---|---|

No marques como verificados elementos que todavía no existen físicamente. Distingue cumplimiento de la propuesta y verificación de implementación.

### 7. Riesgos, observaciones y decisiones pendientes

Menciona únicamente los hallazgos relevantes.

### 8. Solicitud de aprobación

Finaliza preguntando si apruebo el árbol y los comandos antes de implementarlos.

**Detente en este punto.**

---

## Para la ETAPA B

Después de mi aprobación, presenta un informe con:

### 1. Comandos realmente ejecutados

En su orden de ejecución.

### 2. Archivos y carpetas creados

Indica qué se creó y para qué.

### 3. Árbol real del proyecto

Incluye la salida auténtica del comando de terminal.

### 4. Verificaciones

| Verificación | Resultado | Evidencia |
|---|---|---|
| Carpetas obligatorias | | |
| Carpeta Supabase | | |
| Documentación por carpeta | | |
| Nomenclatura | | |
| Separación de responsabilidades | | |
| Coincidencia con ARCHITECTURE.md | | |
| Compilación | | |
| Lint | | |
| Estado de Git | | |

### 5. Desviaciones detectadas

Explica cualquier diferencia respecto del plan, o confirma que no hubo desviaciones si realmente lo comprobaste.

### 6. Confirmación de alcance

Confirma si la estructura quedó implementada, documentada y verificada sin introducir funcionalidades de inventario ni integrar Supabase.

---

# 10. Criterios finales de aceptación

Consideraré satisfactoria esta actividad solamente cuando:

1. La propuesta respete íntegramente `ARCHITECTURE.md`.
2. La estructura haya sido aprobada antes de implementarse.
3. Las carpetas solicitadas existan físicamente.
4. Los cinco archivos `readme.md` documenten responsabilidades claras.
5. Exista una ubicación específica para la futura integración con Supabase.
6. No se hayan instalado dependencias innecesarias.
7. No se hayan implementado funcionalidades fuera del alcance.
8. La salida de `tree` corresponda al proyecto real.
9. `npm run build` y `npm run lint` terminen correctamente.
10. Se pueda demostrar trazabilidad entre especificación, propuesta, implementación y verificación.

Tu objetivo es generar una estructura **mínima, modular, escalable, comprensible para desarrolladores junior y fiel a la metodología SDD**.

**Comienza exclusivamente con la ETAPA A. No ejecutes la ETAPA B hasta recibir mi aprobación.**
