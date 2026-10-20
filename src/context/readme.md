# context

## Propósito
Contextos y proveedores de React para estado transversal que varias partes de la interfaz necesitan compartir.

## Pertenece aquí
- Contextos y sus proveedores, solo cuando el estado realmente se comparte.

## No pertenece aquí
- Estado local de un solo componente.
- Consultas directas a Supabase o acceso a datos, que van en `services/`.

## Relación con otras capas
Puede apoyarse en `hooks/` y `types/`. Los componentes lo consumen mediante hooks.