# hooks

## Propósito
Hooks personalizados que coordinan servicios y gestionan el estado de la interfaz: datos, carga y errores.

## Pertenece aquí
- Funciones cuyo nombre comienza con `use`.
- Llamadas a `services/` y traducción de sus resultados a estado de React.

## No pertenece aquí
- Componentes ni JSX.
- Configuración o uso directo del cliente de Supabase.
- Reglas de negocio ni acceso a datos, que van en `services/`.

## Relación con otras capas
Los consumen `components/` y `context/`. Dependen de `services/` y `types/`.