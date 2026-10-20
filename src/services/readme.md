# services

## Propósito
Operaciones de aplicación y acceso a datos. Es la única capa que consumirá el cliente configurado en `lib/supabase/`.

## Pertenece aquí
- Funciones que ejecutan operaciones de inventario y consultas.
- Transformación de datos entre la base de datos y los tipos de `types/`.

## No pertenece aquí
- JSX o componentes React.
- Hooks de React o estado de la interfaz.
- Creación del cliente de Supabase: se inicializará en `lib/supabase/`, hoy solo reservada con `.gitkeep`.

## Relación con otras capas
Los consumen `hooks/`. Dependen de `types/` y, más adelante, de `lib/supabase/`. Los componentes no deben importarlos.