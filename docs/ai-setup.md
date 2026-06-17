# AI Setup

## Objetivo

Configurar las herramientas de IA para que comprendan el contexto técnico de NoteFlow desde el inicio y generen código consistente con la arquitectura definida.

## Cursor

Se ha creado un archivo `.cursorrules` con:

- Stack tecnológico del proyecto.
- Convenciones de nombres.
- Estructura de carpetas.
- Restricciones arquitectónicas.
- Reglas de estado local.
- Normas de calidad de código.

### Motivo

Reducir inconsistencias y evitar que la IA proponga soluciones incompatibles con el MVP.

## Claude

Prompt persistente configurado con:

- React Native
- Expo
- TypeScript
- Expo Router
- AsyncStorage
- Arquitectura basada en hooks

### Restricciones

- No usar Redux.
- No usar backend.
- No introducir dependencias innecesarias.
- Mantener componentes pequeños y reutilizables.

## Gemini

Configuración equivalente al contexto utilizado en Claude.

### Convenciones

- PascalCase para componentes.
- camelCase para variables.
- Hooks reutilizables.
- Persistencia local mediante AsyncStorage.

## Beneficios

- Respuestas más consistentes.
- Menos refactorizaciones.
- Mayor alineación con la arquitectura del proyecto.
- Desarrollo más rápido y predecible.