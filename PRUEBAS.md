# Pruebas

| ID | Requisito | Orden o secuencia | Resultado esperado | Resultado obtenido | OK |
|---|---|---|---|---|---|
| P01 | R1 | `registrar @kiwi` (dos veces) | La segunda vez: `E: No se pudo registrar @kiwi` | 1.a vez: `Registrado: @kiwi (id 10)`; 2.a vez: `E: No se pudo registrar @kiwi` | Si |
| P02 | R1 | `registrar kiwi` (sin @) | `E: No se pudo registrar kiwi` | `E: No se pudo registrar kiwi` | Si |
| P03 | R2 | `arbol` (al iniciar, con la ficha) | `Preorden: @nube @delta @chasqui @cactus @neon @haiku @koala @turbo @sushi @orbita` y `Nodos: 10 \| altura: 5 \| hojas: 3` | Igual al esperado | Si |
| P04 | R3 | `seguir @a @a` | `E: Una cuenta no puede seguirse a si misma` | Con `seguir @nube @nube`: `E: Una cuenta no puede seguirse a si misma` (con `@a` literal sale `E: No existe @a`, porque `@a` no esta en la comunidad) | Si |
| P05 | R4 | `popular` (al iniciar) | `Popular: @koala \| seguidores: 4` | Pendiente (R4, v1.0) |  |
| P06 | R5 | `alcance @chasqui` (al iniciar) | `Alcance de @chasqui: @neon @cactus @orbita @haiku \| alcanzados: 4` | Pendiente (R5, v1.0) |  |
| P07 | R6 | `guardar`, `salir`, abrir, `cargar`, `arbol` | El mismo preorden, la misma altura y los mismos seguimientos | Pendiente (R6, v1.0) |  |
| P08 | R7 | `hola`, `seguir`, `perfil @nadie` | Mensajes de error; el programa sigue | `hola: orden no encontrada (escribe ayuda)`, `Uso: seguir @a @b`, `E: No existe @nadie`; el programa sigue | Si |
| P09 | R1 | `usuarios` (al iniciar) | `Usuarios (enorden): @cactus @chasqui @delta @haiku @koala @neon @nube @orbita @sushi @turbo` | Igual al esperado | Si |
| P10 | R1 · R3 | `perfil @cactus` | `@cactus \| id 9 \| seguidores 2 \| siguiendo 3` | Igual al esperado | Si |
| P11 | R3 | `seguidores @cactus` (punto de control de la ficha) | `Seguidores de @cactus (2): @orbita @haiku` | Igual al esperado | Si |
| P12 | R1 | `registrar @jazz` | `Registrado: @jazz (id 10)` | Igual al esperado | Si |
| P13 | R2 | `arbol` despues de registrar `@jazz` | `Preorden: @nube @delta @chasqui @cactus @neon @haiku @koala @jazz @turbo @sushi @orbita` y `Nodos: 11 \| altura: 6 \| hojas: 3` | Igual al esperado | Si |
| P14 | R3 | `seguir @chasqui @jazz` (dos veces) | 1.a vez: `@chasqui ahora sigue a @jazz`; 2.a vez: `E: @chasqui ya sigue a @jazz` | Igual al esperado | Si |
| P15 | R3 | `dejar @neon @chasqui` | `@neon dejo de seguir a @chasqui` | Igual al esperado | Si |
| P16 | R3 | `dejar @nube @neon` (no lo sigue) | `E: @nube no sigue a @neon` | Igual al esperado | Si |
| P17 | R3 | `seguir @x @nube` (cuenta que no existe) | `E: No existe @x` | Igual al esperado | Si |
| P18 | R3 | `seguidores @neon` (nadie la sigue) | `Seguidores de @neon (0): (nadie)` | Igual al esperado | Si |
| P19 | R1 | `registrar @Jazz` (mayuscula) | `E: No se pudo registrar @Jazz` | Igual al esperado | Si |
| P20 | R1 | `registrar @abcdefghijklmnop` (16 caracteres despues de @) | `E: No se pudo registrar @abcdefghijklmnop` | Igual al esperado | Si |
| P21 | R1 | `registrar` (sin argumento) | `Uso: registrar @usuario` | Igual al esperado | Si |
| P22 | R1 | Registrar 3 cuentas nuevas (`@a1`, `@a2`, `@a3`) con 10 cargadas | `@a1` id 10, `@a2` id 11 y `@a3` rechazada (MAX = 12) | `Registrado: @a1 (id 10)`, `Registrado: @a2 (id 11)`, `E: No se pudo registrar @a3` | Si |
| P23 | R1 a R3 | Secuencia oficial completa (`pruebas/secuencia.txt`) | Las lineas de `pruebas/esperado.txt` | Las 17 lineas aparecen en la salida | Si |
| P24 | R4 | `mutuos @cactus` | `Mutuos de @cactus (1): @haiku` | Igual al esperado | Si |
| P25 | R4 | `popular` despues de `seguir @jazz @nube` (empate @nube y @koala con 4) | `Popular: @nube \| seguidores: 4` (gana el menor id) | Igual al esperado | Si |
| P26 | R5 | `llega @chasqui @orbita` y `llega @cactus @delta` | `si` y `no` | `Un post de @chasqui llega a @orbita: si` y `Un post de @cactus llega a @delta: no` | Si |
| P27 | R5 | `alcance @chasqui` despues de `dejar @neon @chasqui` | `Alcance de @chasqui: @cactus @orbita @haiku \| alcanzados: 3` | Igual al esperado | Si |
| P28 | R5 | `alcance @neon` (nadie la sigue) | `Alcance de @neon: (nadie) \| alcanzados: 0` | Igual al esperado | Si |
| P29 | R5 | `llega @nube @nube` | `E: Elijan dos cuentas distintas` | Igual al esperado | Si |
| P30 | R5 | `llega @nube` (falta una cuenta) | `Uso: llega @a @b` | Igual al esperado | Si |
| P31 | R5 | `llega @neon @nube` (el sentido importa) | `Un post de @neon llega a @nube: no` | Igual al esperado | Si |
| P32 | R6 | `guardar` y revisar `nido.txt` | 11 lineas `U` en preorden y 17 lineas `S` por filas | `Guardado: 11 cuentas y 17 seguimientos en nido.txt`; archivo en `pruebas/nido.txt` | Si |
| P33 | R6 | `cargar` en un programa recien abierto, luego `perfil @jazz` | `@jazz` conserva su id 10 y sus seguimientos | `Cargado: 11 cuentas y 17 seguimientos \| altura 6` y `@jazz \| id 10 \| seguidores 1 \| siguiendo 1` | Si |
| P34 | R7 | `reporte` (despues de la secuencia) | `Cuentas: 11 \| seguimientos: 17 \| pares mutuos: 2` y `Arbol: altura 6 \| hojas 3` | Igual al esperado | Si |
| P35 | R7 | `salir` | `Nodos liberados: 11. Hasta pronto.` | Igual al esperado | Si |
| P36 | R7 | Linea vacia, `HOLA @x`, `registrar @a-b`, `registrar @` | Ninguna cierra el programa | Linea vacia: vuelve a pedir orden; `HOLA: orden no encontrada (escribe ayuda)`; `E: No se pudo registrar @a-b`; `E: No se pudo registrar @` | Si |

Agreguen todas las que necesiten. Incluyan casos con datos invalidos.
