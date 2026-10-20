# components

## Propósito
Componentes React de presentación e interacción con el usuario.

## Pertenece aquí
- Componentes funcionales con JSX (identificadores en `PascalCase`).
- Estado visual local (por ejemplo, un menú abierto o cerrado).

## No pertenece aquí
- Consultas a Supabase o importación del cliente de `lib/supabase`.
- Reglas de negocio u orquestación de datos.

## Relación con otras capas
Obtiene datos y acciones a través de `hooks/` y usa contratos de `types/`. No importa `services/` directamente.