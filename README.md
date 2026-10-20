# EcoTech Inventory SDD

Andamiaje arquitectónico (*scaffolding*) para una futura aplicación de **gestión de inventario sostenible** de **EcoTech Solutions**. Proyecto académico del curso **El Arquitecto IA: Desarrollo Basado en Especificaciones con React y Supabase** (ADA).

> **Estado actual:** estructura y documentación iniciales completadas. **No** se han implementado inventario funcional, CRUD, autenticación ni conexión a Supabase.

## Stack

- **Frontend:** React + Vite + TypeScript.
- **Análisis estático:** Oxlint (según la plantilla instalada).
- **Integración futura:** Supabase (sin dependencia ni credenciales configuradas por ahora).

## Requisitos y ejecución local

Se requiere Node.js y npm compatibles con la versión de Vite indicada en `package.json`.

```bash
npm install
npm run dev
```

Vite mostrará en la terminal la URL local de desarrollo. Para validar el proyecto:

```bash
npm run build
npm run lint
```

El build genera `dist/`, que no debe versionarse.

## Arquitectura

```text
src/
├── App.tsx
├── main.tsx
├── index.css
├── components/       # Componentes de presentación
│   └── readme.md
├── hooks/            # Hooks personalizados y estado de UI
│   └── readme.md
├── services/         # Operaciones de aplicación y acceso a datos
│   └── readme.md
├── types/            # Contratos TypeScript compartidos
│   └── readme.md
├── context/          # Estado transversal y proveedores
│   └── readme.md
└── lib/
    └── supabase/    # Configuración futura del cliente Supabase
        └── .gitkeep
```

La estructura se organiza **por responsabilidades** para facilitar el trabajo de un equipo junior. El flujo de dependencias previsto es `components → hooks → services → lib/supabase`, con tipos compartidos en `types/` y estado transversal en `context/` cuando se necesite.

Los componentes no deben consultar Supabase directamente ni contener reglas de negocio. Los servicios concentrarán el futuro acceso a datos; `lib/supabase` alojará la configuración del cliente. Cada carpeta principal incluye su `readme.md` con responsabilidades, restricciones y relaciones.

## Desarrollo basado en especificaciones (SDD)

El plano del proyecto es **[`ARCHITECTURE.md`](./ARCHITECTURE.md)**. La estructura se propuso mediante un Prompt Maestro, se auditó y aprobó antes de crear las carpetas, y posteriormente se verificó mediante el árbol de directorios, compilación y lint.

El objetivo es mantener **trazabilidad entre especificación, planificación, implementación y verificación**, evitando dependencias indebidas y deuda técnica desde el inicio.

## Alcance de esta entrega

**Incluye:** entorno React + Vite + TypeScript, limpieza del ejemplo inicial, documento de arquitectura, carpetas estructurales y documentación breve de cada responsabilidad.

**No incluye:** lógica de inventario, formularios, CRUD, tablas PostgreSQL, políticas RLS, autenticación, configuración de claves ni cliente Supabase operativo.

Las funcionalidades de productos, movimientos de inventario y reportes podrán incorporarse en etapas futuras, respetando las reglas descritas en `ARCHITECTURE.md`.
