````md
# Centlalia

## Estado actual del proyecto y propuesta de incubación

Centlalia nació como un proyecto de hackathon dentro del ecosistema WayLearn.

Durante el hackathon construimos una primera versión funcional enfocada en **ticketing sobre Solana**. Esta versión nos permitió probar una idea inicial: usar assets digitales, principalmente NFTs/cNFTs, para representar tickets de eventos y controlar su ciclo de vida mediante un programa on-chain.

Sin embargo, el aprendizaje más importante del hackathon fue más grande que ticketing:

> Un asset por sí solo no representa su validez.

Un NFT puede existir.  
Puede estar en una wallet.  
Puede tener metadata.  
Puede haber sido emitido correctamente.

Pero eso no significa automáticamente que sea válido para una acción específica.

Por ejemplo, en ticketing:

- tener el NFT no siempre significa poder entrar;
- el ticket puede haber sido usado;
- puede no pertenecer al holder reconocido;
- puede estar fuera de las reglas del evento;
- puede haber sido transferido de forma no reconocida por el protocolo;
- puede requerir validación por un staff autorizado.

Ese aprendizaje es la base de la nueva etapa de Centlalia.

---

## Links del hackathon

- Proyecto en DoraHacks: https://dorahacks.io/buidl/41766  
  Password: `#WayLearn2026`

- Repositorio actual: https://github.com/MelenoiddCoding/centlalia

---

# 1. Dónde estamos ahorita

El estado actual de Centlalia es un **MVP de hackathon**.

No es todavía un producto final.

No es todavía una arquitectura completamente separada por módulos.

No es todavía una capa general de validación lista para múltiples casos de uso.

Lo que existe hoy es una primera implementación funcional enfocada en ticketing, construida para validar la idea técnica y demostrar que podemos controlar más que solo la emisión de un NFT.

Actualmente el proyecto cuenta con:

- un programa Anchor en Solana;
- una dapp web;
- scripts de operación en devnet;
- integración con NFTs/cNFTs;
- registro protocolar de tickets;
- flujo de creación de eventos;
- flujo de compra primaria;
- flujo de reventa;
- flujo de validación/check-in;
- separación inicial entre asset y validez reconocida.

El Program ID actual en devnet es:

```txt
9KBJPw5xHEirJDwW9aSaDbVTf9sP9NuRu1oMSqjTsq8b
````

---

# 2. Qué construimos en el hackathon

Durante el hackathon construimos una versión de Centlalia enfocada en **ticketing programable**.

La lógica principal permite:

```txt
Crear evento
Crear tiers
Publicar evento
Comprar ticket
Emitir/relacionar asset digital
Registrar ticket dentro del protocolo
Reconocer holder válido
Permitir transferencia/reconocimiento bajo reglas
Listar ticket en reventa
Comprar ticket en reventa
Autorizar staff
Validar ticket en acceso
Marcar ticket como usado
```

El objetivo no era construir una boletera completa lista para producción.

El objetivo era demostrar que un ticket puede tener una capa de control superior al asset.

---

# 3. Qué aprendimos

El hackathon nos dejó una conclusión central:

> El NFT o asset no debe ser la fuente única de verdad.

El asset representa algo.

Pero la validez necesita más contexto.

Necesita saber:

```txt
Quién lo emitió
Quién lo tiene
Quién está reconocido como holder válido
Qué reglas aplican
Qué dice el registro del protocolo
Quién está intentando validarlo
Qué acción se quiere validar
```

En ticketing, esto se vio muy claro.

Un ticket no es válido solo porque está en una wallet.

Un ticket es válido si el sistema puede comprobar que:

```txt
El issuer es correcto
El holder presentado coincide con la verdad registrada
Las políticas del evento se cumplen
El ticket no ha sido consumido
La acción solicitada es válida
El validator tiene el contexto correcto para verificar
```

Este aprendizaje abre la puerta a una visión más general de Centlalia.

---

# 4. Qué es Centlalia hoy

Hoy Centlalia es:

> Un MVP de ticketing verificable sobre Solana.

También es:

> Una primera prueba de concepto de una capa más general para validar assets digitales bajo reglas.

La versión actual está parada entre dos etapas:

```txt
Hackathon MVP
      ↓
Incubación
      ↓
Arquitectura general de validación
      ↓
Primer producto: Ticketing
```

---

# 5. Qué no es Centlalia todavía

Es importante ser claros.

Centlalia todavía no es:

* una boletera lista para producción;
* una capa universal de validación terminada;
* un estándar completo;
* una plataforma multi-industria;
* una solución final de membresías, transporte o credenciales;
* un protocolo auditado para mainnet.

La etapa actual es de exploración técnica, validación de arquitectura y evolución del MVP.

---

# 6. Propuesta para incubación

La propuesta de incubación es tomar lo aprendido en el hackathon y convertirlo en una arquitectura más clara, más general y más preparada para producto.

No queremos trabajar únicamente en “mejorar la boletera”.

Queremos trabajar en Centlalia como:

> Una capa de validación para assets digitales, usando ticketing como primer caso de uso real.

Ticketing seguirá siendo importante porque es el caso donde ya tenemos más avance.

Pero la incubación debe enfocarse en entender y diseñar bien la base general.

---

# 7. Dirección general de Centlalia

La dirección propuesta es:

```txt
Centlalia = capa de validación para assets digitales
Ticketing = primer caso de uso construido sobre esa capa
```

Esto significa que el sistema debe poder responder preguntas como:

```txt
¿Este asset es válido?
¿Para quién es válido?
¿Bajo qué reglas?
¿Quién lo emitió?
¿Qué dice el Registry?
¿Qué está intentando validar el Validator?
¿Qué resultado produce la validación?
```

No solo para tickets.

También para otros casos donde se necesite validar algo:

* membresías;
* permisos;
* credenciales;
* transporte;
* accesos;
* beneficios;
* certificaciones;
* cupones;
* licencias;
* pases temporales.

---

# 8. Modelo general propuesto

La propuesta conceptual para incubación se basa en estos componentes:

```txt
Issuer
Holder
Asset
Policies
Registry
Validator
Validation
```

---

## Issuer

El **Issuer** es quien emite o reconoce un asset.

Puede ser:

```txt
Una boletera
Una escuela
Una empresa
Una comunidad
Un sistema de transporte
Un organizador
Un protocolo externo
Centlalia
```

El Issuer puede usar Centlalia para emitir el asset, o puede emitirlo por fuera y solamente registrar su validez dentro de Centlalia.

Esto es importante porque Centlalia no debe depender de que todos los assets sean creados por la propia plataforma.

---

## Holder

El **Holder** es quien posee o presenta el asset.

En algunos casos, el holder será simplemente la wallet que tiene el NFT.

Pero en otros casos, puede haber una diferencia entre:

```txt
Holder técnico
Holder reconocido
Holder presentado
```

Esto es clave porque la posesión técnica del asset no siempre debe equivaler a validez.

---

## Asset

El **Asset** es el objeto digital.

Puede ser:

```txt
NFT
cNFT
Token
Credential
QR
Pase
Permiso
Membresía
Asset externo
```

El asset por sí solo no define si algo es válido.

El asset es una referencia.

La validez se obtiene al contrastar ese asset contra el Registry y las Policies.

---

## Policies

Las **Policies** son el set de reglas que define qué significa que algo sea válido.

Ejemplos:

```txt
El holder debe coincidir con el holder reconocido
El issuer debe ser válido
El asset debe estar activo según el Registry
El asset no debe estar expirado
El asset no debe estar revocado
El validator debe tener permiso
La acción solicitada debe estar permitida
La validación debe ocurrir dentro de una ventana específica
```

Las Policies no son iguales para todos los casos.

Ticketing tiene sus propias reglas.

Membresías tienen otras.

Transporte tendría otras.

Credenciales tendrían otras.

Por eso Centlalia no debe hardcodear una sola forma de validez.

---

## Registry

El **Registry** es donde se guarda la verdad que el Validator necesita consultar.

El Registry puede guardar información sobre:

```txt
Asset
Issuer
Holder reconocido
Relación asset-holder
Policies aplicables
Facts específicos del dominio
```

El Registry no debe asumir que todos los casos funcionan igual.

Por ejemplo, en ticketing puede guardar información relacionada con evento, tier, reventa o check-in.

En membresías puede guardar plan, nivel o expiración.

En transporte puede guardar ruta, zona o periodo de validez.

La idea es:

> El Registry guarda la verdad.
> Las Policies interpretan esa verdad.

---

## Validator

El **Validator** es quien necesita validar algo.

Puede ser:

```txt
Staff de un evento
Una app de transporte
Una escuela
Una empresa
Un comercio
Una comunidad
Un contrato
Un backend externo
Un usuario
```

El Validator no necesariamente controla el asset.

El Validator solicita una validación.

Por ejemplo:

```txt
¿Este ticket permite entrar?
¿Esta membresía permite acceder?
¿Esta credencial sigue siendo válida?
¿Este pase puede usarse en esta ruta?
```

---

## Validation

La **Validation** es el proceso donde se contrasta:

```txt
Lo que presenta el Holder
+
Lo que dice el Registry
+
Lo que exigen las Policies
+
Lo que solicita el Validator
```

Y produce un resultado:

```txt
Válido
Inválido
Rechazado por policy
Holder incorrecto
Issuer inválido
Asset no reconocido
Contexto insuficiente
```

Esta parte todavía debe diseñarse durante la incubación.

Una posibilidad es trabajar con:

```txt
Validation Blueprints
SDK de validación
Funciones on-chain
Validación off-chain
Validación híbrida
```

La decisión depende de qué tan general queremos que sea la capa y qué partes deben estar on-chain o fuera de chain.

---

# 9. Cómo encaja ticketing en este modelo

Ticketing es el primer caso de uso.

En ticketing, los componentes se ven así:

```txt
Issuer = organizador / boletera
Holder = asistente
Asset = ticket NFT/cNFT
Policies = reglas del evento
Registry = verdad del ticket
Validator = staff / scanner
Validation = check-in
```

El dominio ticketing agrega cosas específicas:

```txt
Evento
Venue
Fechas
Tiers
Precio
Supply
Reventa
Royalty
Fee
Staff
Check-in
```

Estas cosas no pertenecen a la capa general.

Pertenecen al producto ticketing.

---

# 10. Qué sigue para ticketing durante incubación

Aunque la visión se vuelva más general, ticketing sigue siendo el caso de uso principal para probar la arquitectura.

Durante la incubación se propone trabajar en:

## Mejorar el contrato actual

* Separar reglas de reventa.
* Separar fee de plataforma de royalty del organizador.
* Mejorar lifecycle de evento.
* Definir cancelación, finalización e invalidación.
* Mejorar manejo de holders reconocidos.
* Formalizar qué significa transferir un ticket.
* Endurecer la validación de acceso.

## Mejorar la experiencia de producto

* Dashboard de organizador.
* Vista pública de evento.
* Compra de tickets.
* Vista de mis tickets.
* Flujo de reventa.
* Flujo de transferencia.
* Scanner de acceso.

## Construir scanner

El scanner debe convertirse en una pieza clara del sistema.

Debe poder validar:

```txt
Ticket existe
Ticket pertenece al evento
Holder coincide
Ticket cumple policies
Ticket no fue usado
Staff puede validar
Resultado final
```

## Crear SDK o capa de integración

Para que otros puedan usar Centlalia, se necesita una forma clara de interactuar con:

```txt
Registry
Policies
Validation
Ticketing
```

Esto puede iniciar como SDK interno para la dapp y luego abrirse.

---

# 11. Qué sigue para la capa general

La incubación también debe avanzar en la arquitectura general.

Preguntas a resolver:

```txt
¿Cómo se define un Issuer?
¿Cómo se registra un asset externo?
¿Cómo se define una Policy?
¿Qué información mínima debe tener el Registry?
¿Qué parte de la validación vive on-chain?
¿Qué parte puede vivir en SDK?
Cómo se representa una ValidationRequest?
Cómo se representa un ValidationResult?
Cómo se manejan distintos dominios?
Cómo evitamos hacer una arquitectura demasiado genérica?
```

La meta no es construir todos los casos de uso al mismo tiempo.

La meta es diseñar una base suficientemente clara para que ticketing no quede encerrado como una boletera NFT.

---

# 12. Propuesta de arquitectura para incubación

Durante incubación, el proyecto puede dividirse así:

```txt
Centlalia Core
Capa de validación general.

Centlalia Ticketing
Primer módulo/producto sobre Core.

Centlalia SDK
Herramientas para leer registry, construir requests y validar.

Centlalia Scanner
Primer validator real para ticketing.

Centlalia App
Frontend para organizadores y holders.
```

Una estructura posible del repo:

```txt
centlalia/
├── programs/
│   ├── core/
│   └── ticketing/
├── apps/
│   ├── web/
│   └── scanner/
├── packages/
│   ├── sdk/
│   └── validation/
├── scripts/
├── docs/
└── README.md
```

Esto no significa reescribir todo desde cero.

Significa ordenar el proyecto para poder evolucionarlo.

---

# 13. Objetivo de la incubación

El objetivo de la incubación es pasar de:

```txt
MVP de hackathon enfocado en ticketing
```

a:

```txt
Base clara de validación + primer producto ticketing funcional
```

La meta no es prometer que Centlalia ya resuelve todos los tipos de validación.

La meta es demostrar que:

```txt
1. El modelo asset + registry + policies + validator tiene sentido.
2. Ticketing es un buen primer caso de uso.
3. La arquitectura puede extenderse a otros dominios.
4. Centlalia puede convertirse en infraestructura, no solo en dapp.
```

---

# 14. Resumen

Centlalia hoy está en etapa post-hackathon.

Lo construido demuestra un sistema de ticketing sobre Solana con assets digitales, registro protocolar, reventa y validación.

Pero el aprendizaje principal es más amplio:

> La validez no vive solamente en el NFT.

La nueva propuesta para incubación es desarrollar Centlalia como una capa general de validación para assets digitales, usando ticketing como primer caso de uso.

El modelo base es:

```txt
Issuer
Holder
Asset
Policies
Registry
Validator
Validation
```

Ticketing será el primer vertical.

La capa general será el trabajo principal de diseño durante la incubación.

Centlalia no busca ser solo una boletera NFT.

Busca convertirse en una infraestructura para responder una pregunta más grande:

> ¿Esto que alguien presenta es válido para la acción que quiere realizar?

```

Esta versión sí deja más claro el punto correcto: **hackathon primero, incubación después, y modelo general como propuesta de trabajo, no como algo ya terminado.**
```
