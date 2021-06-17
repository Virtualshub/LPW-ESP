---
description: 'Woonkly implementa los siguientes protocolos de consenso:'
---

# Protocolo de consenso IFBT 2.0



* [IBFT 2.0](https://besu.hyperledger.org/en/stable/HowTo/Configure/Consensus-Protocols/IBFT/) \(Proof of Authority\)

La propiedad config en el archivo genesis especifica el protocolo de consenso para una cadena.

```text
{
  "config": {
   ...
    "ibft2": {
     ...
   }
  },
  ...
}
```

Los protocolos de consenso de prueba de autoridad funcionan cuando los participantes se conocen entre sí y existe un nivel de confianza entre ellos. Por ejemplo, en una red de consorcio autorizada.

Los protocolos de consenso de Prueba de Autoridad tienen tiempos de bloqueo más rápidos y un rendimiento de transacciones mucho mayor que el protocolo de consenso de Prueba de Trabajo de Ethash utilizado en la red principal de Ethereum.

En Clique e IBFT 2.0, un grupo de nodos de la red actúan como firmantes \(Clique\) o validadores \(IBFT 2.0\). Los nodos existentes en el grupo de firmantes/validadores votan para añadir o eliminar nodos del grupo.

## Nota

En el resto de esta página, el término validador se utiliza para referirse a los firmantes y validadores.

Las propiedades que hay que tener en cuenta al comparar Clique e IBFT 2.0 son:

Finalidad inmediata Número mínimo de validadores Capacidad de respuesta Rapidez. Finalidad inmediata IBFT 2.0 tiene finalidad inmediata. Al utilizar IBFT 2.0 no hay bifurcaciones y todos los bloques válidos se incluyen en la cadena principal.

Clique: no tiene finalidad inmediata. Las implementaciones que utilizan Clique deben ser conscientes de las bifurcaciones y reorganizaciones de la cadena que se producen.

Número mínimo de validadores: Para ser tolerante a fallos bizantinos, el IBFT 2.0 requiere un mínimo de cuatro validadores.

Clique puede operar con un solo validador, pero operar con un solo validador no ofrece redundancia si el validador falla.

## IFBT

La tolerancia a fallos bizantina es la capacidad de funcionar correctamente y alcanzar el consenso a pesar de que los nodos fallen o propaguen información incorrecta a los compañeros.

 Las redes IBFT 2.0 requieren que dos tercios de los validadores funcionen para crear bloques. Por ejemplo, una red IBFT 2.0 de:

De cuatro a cinco validadores tolera un validador que no responde. De seis a ocho validadores tolera dos validadores que no responden. Las redes con tres o menos validadores pueden producir bloques, pero no garantizan la finalidad cuando operan en entornos adversos.



