---
description: >-
  Todos los nodos mantienen un pool de transacciones para almacenar las
  transacciones pendientes antes de su procesamiento
---

# Pool de transacciones

#### Las opciones y métodos para configurar y monitorizar el pool de transacciones incluyen

```javascript
txpool_besuTransactions Método de la API JSON-RPC para listar las transacciones en
el pool de transacciones.

--tx-pool-max-size opción de línea de comandos para especificar el número máximo 
de transacciones en el pool de transacciones.

--tx-pool-hashes-max-size opción de línea de comandos para especificar el número 
máximo de hashes de transacciones en el pool de transacciones. 
Debe ser mayor o igual que el valor especificado para --tx-pool-max-size.

Opción de línea de comandos --tx-pool-price-bump para especificar el porcentaje 
de aumento de precio para reemplazar una transacción existente.


Opción de línea de comandos --tx-pool-retention-hours para especificar el número 
máximo de horas para mantener las transacciones pendientes en el pool 
de transacciones.
newPendingTransactions y droppedPendingTransactions Suscripciones RPC para 
notificar las transacciones añadidas y retiradas del pool de transacciones.


```

#### Importante

Cuando se envían transacciones privadas, la transacción del marcador de privacidad se envía al pool de transacciones, no la transacción privada en sí.

#### Eliminación de transacciones cuando el pool de transacciones está lleno

Cuando el pool de transacciones está lleno, acepta y retiene las transacciones locales con preferencia a las remotas. Si el pool de transacciones está lleno de transacciones locales, Besu elimina primero las transacciones locales más antiguas. Es decir, un pool de transacciones lleno sigue aceptando nuevas transacciones locales, eliminando primero las transacciones remotas y luego las transacciones locales más antiguas.

#### Sustitución de transacciones con el mismo remitente y nonce

Para las transacciones recibidas con el mismo remitente y nonce que una transacción pendiente pero con un precio del gas superior al existente en el porcentaje especificado por --tx-pool-price-bump, Besu sustituye la transacción pendiente por la nueva con el precio del gas más alto. El valor por defecto de --tx-pool-price-bump es el 10%.

#### Tamaño del pool de transacciones

Disminuir el tamaño máximo del pool de transacciones reduce el uso de memoria. Si la red está ocupada y hay una acumulación de transacciones, podemos aumentar el tamaño del pool de transacciones y reducir el riesgo de eliminar transacciones del pool de transacciones.

