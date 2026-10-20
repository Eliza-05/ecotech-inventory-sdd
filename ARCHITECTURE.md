# Especificación de arquitectura — EcoTech Inventory SDD

## 1. Propósito y alcance

EcoTech Solutions desarrollará una aplicación de gestión de inventario sostenible con React, Vite y TypeScript, preparada para integrar Supabase posteriormente. Esta entrega comprende solo el andamiaje inicial: no incluye pantallas de inventario, operaciones CRUD, autenticación ni una conexión real a la base de datos. La arquitectura debe guiar a un equipo junior y evitar que mezcle presentación, lógica de aplicación y acceso a datos.

## 2. Enfoque arquitectónico

Se adopta una organización por capas de responsabilidad, sencilla de comprender y verificar. Frente a una estructura basada en funcionalidades, esta elección evita crear módulos vacíos antes de implementar funcionalidades. La separación de preocupaciones establece límites explícitos entre interfaz, comportamiento y persistencia.

## 3. Responsabilidades de las carpetas

- `src/components/`: componentes React de presentación e interacción. Pueden manejar estado visual local, pero no ejecutan consultas a Supabase ni reglas de negocio.
- `src/hooks/`: hooks personalizados que coordinan servicios y gestionan estado, carga y errores de la interfaz.
- `src/services/`: operaciones de aplicación y acceso a datos; no contiene JSX ni hooks de React.
- `src/types/`: interfaces y contratos TypeScript compartidos entre capas.
- `src/context/`: contextos y proveedores de estado transversal, cuando sea necesario.

Cada carpeta principal tendrá un `readme.md` con su responsabilidad y restricciones. No se crearán `index.ts` vacíos.

## 4. Integración futura con Supabase

`src/lib/supabase/` reservará la configuración y el cliente compartido de Supabase, mientras que `services/` concentrará las operaciones de inventario. La dirección prevista es `components → hooks → services → lib/supabase`; `types/` proporciona contratos compartidos y `context/` administra estado transversal. La interfaz no importará el cliente ni accederá directamente a la base de datos.

Centralizar estas consultas evita duplicarlas en varios componentes: un cambio posterior en Supabase afectará principalmente a la capa de servicios, reduciendo acoplamiento, retrabajo y deuda técnica.

En esta fase, la carpeta de Supabase tendrá únicamente `.gitkeep`, sin dependencias, credenciales ni código de integración.

## 5. Crecimiento, convenciones y verificación SDD

La estructura permite añadir módulos de productos, movimientos de inventario y reportes mediante componentes, hooks y servicios separados. Cuando existan varios módulos con suficiente complejidad, se podrá evaluar agruparlos por dominio, conservando las reglas de separación.

Las nuevas carpetas y archivos usarán minúsculas y `kebab-case`, conservando excepciones generadas por Vite, como `App.tsx`. Los identificadores de componentes React usarán `PascalCase` y las futuras tablas PostgreSQL, `snake_case`.

Este documento será la fuente de verdad: antes de crear carpetas, la IA propondrá un árbol para aprobación humana. Después se contrastarán rutas, nombres y documentación con la especificación y se ejecutarán `npm run build` y `npm run lint`. Así, los errores de estructura se detectarán antes de convertirse en problemas de mantenimiento.
