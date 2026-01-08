+++
title = "Financiamiento sostenible para el desarrollo de Mostro"
date = "2026-01-08T12:00:00Z"

[extra]
author = "catrya"
img = "/img/dev-fee.jpg"
summary = "Mostro incorpora un sistema de financiamiento automático y transparente para su desarrollo: cada operador de una instancia de Mostro dedica automáticamente un porcentaje configurable de las comisiones que gana a un fondo de desarrollo, sin costos adicionales para los usuarios. Todo el proceso es verificable públicamente mediante eventos publicados en Nostr, alineando incentivos y garantizando la sostenibilidad del proyecto."
+++

El desarrollo de software libre y descentralizado se enfrenta a una pregunta incómoda pero inevitable:  
**¿cómo se financia sin perder independencia, privacidad o descentralización?**

En Mostro decidimos no esquivar ese problema. En lugar de depender de donaciones esporádicas, sponsors o estructuras centralizadas, diseñamos un sistema que se integra de forma natural al funcionamiento de la red y se cuida solo.

## El desafío del financiamiento descentralizado

Desarrollar y mantener una plataforma de intercambio peer-to-peer como Mostro requiere recursos constantes: nuevas funcionalidades, corrección de errores, mejoras de seguridad, auditorías de código y documentación. Tradicionalmente, este tipo de proyectos depende de donaciones voluntarias o financiamiento externo. El problema es que esos modelos suelen ser **impredecibles**, poco sostenibles en el tiempo o generan dependencias que van en contra del espíritu descentralizado.

Necesitábamos algo distinto. Un sistema que fuera:

- **Automático**, sin depender de la buena voluntad de las personas, sin recordatorios ni campañas
- **Transparente**: Totalmente auditable por cualquiera
- **Justo**: Sin cargar costos adicionales a los usuarios finales
- **Descentralizado**: Sin crear puntos centralizados de control

## La idea clave: contribuir desde las ganancias, no desde el uso

La solución que implementamos es conceptualmente simple pero técnicamente sofisticada.

Cada operador de una instancia de Mostro puede configurar un porcentaje (mínimo 10%, por defecto 30%) de las comisiones que **él mismo gana** para que sean donadas automáticamente al fondo de desarrollo.

### Un ejemplo concreto

Imaginemos una operación típica:

- **Monto del intercambio**: 100,000 sats  
- **Comisión total**: 1,000 sats (1%, repartido entre comprador y vendedor, aunque la comisión de cada instancia la decide su operador)  
- **Dev fee configurado**: 30%  
- **Contribución al desarrollo**: 300 sats  

**Lo importante**: Los 300 sats los paga la instancia de Mostro desde sus ganancias, **no se cargan al usuario**. El comprador sigue pagando exactamente los mismos 500 sats de comisión, el vendedor otros 500 sats, y Mostro dona 300 sats de los 1,000 que recibió.

## Transparencia total mediante Nostr

Un sistema así solo funciona si puede ser auditado sin pedir permiso. Por eso, cada contribución al fondo de desarrollo genera automáticamente un evento público en **Nostr**.

Ese evento incluye:

- El monto aportado
- El hash del pago en Lightning
- El timestamp exacto
- La referencia a la orden que lo originó

Estos eventos se publican usando un tipo específico (`kind 8383`), lo que permite a cualquiera reconstruir el historial completo de contribuciones y verificar que el sistema funciona exactamente como se describe.

No hay reportes internos. No hay promesas. **Hay datos verificables.**

## Un sistema que funciona en segundo plano

Una vez configurado, el mecanismo es completamente automático:

1. El operador define su porcentaje (entre 10% y 100%)
2. Cada operación exitosa genera una contribución
3. Un scheduler interno procesa los pagos cada 60 segundos
4. Los eventos se publican en Nostr
5. Si algo falla, las operaciones continúan normalmente

Nada de esto interfiere con la experiencia del usuario ni con el flujo de los intercambios.

## Incentivos alineados para todos

Este modelo genera beneficios para todos los participantes.

### Operadores de Mostro
- Contribuyen al desarrollo de la herramienta que les genera ingresos
- Mantienen control total sobre su porcentaje de contribución
- Obtienen transparencia completa sobre sus aportes

### Usuarios
- No pagan comisiones adicionales
- Usan una plataforma que mejora constantemente
- Pueden verificar públicamente cómo se financia el proyecto

### Proyecto
- Obtiene financiamiento predecible
- Incentivos alineados: más uso significa más financiamiento
- Mantiene independencia y transparencia

## Implementación técnica sin sorpresas

Para quienes quieran profundizar, el sistema contempla:

- Cálculo unificado de comisiones para distintos tipos de órdenes
- Pagos asíncronos que no bloquean operaciones
- Manejo de condiciones de carrera
- Recuperación automática de órdenes abandonadas
- Validaciones robustas y timeouts bien definidos

Todo el código es público, forma parte del repositorio principal de Mostro y la documentación técnica detalla cada aspecto de la implementación.


## Más que un dev fee: un modelo de sostenibilidad

Este sistema no es solo una forma de financiar desarrollo. Es una demostración práctica de que los proyectos descentralizados pueden sostenerse sin sacrificar sus principios.

- **Sin dependencias externas**: Los fondos provienen del ecosistema mismo
- **Sin puntos centralizados de fallo**: Cada operador decide su nivel de contribución
- **Sin costos para usuarios finales**: Las contribuciones salen de las ganancias, no de nuevas comisiones
- **Con total transparencia**: Toda la información es públicamente auditable

## Conclusión

El sistema de dev fee de Mostro demuestra que es posible combinar sostenibilidad económica con principios descentralizados. Al automatizar las contribuciones y hacer todo el proceso transparente mediante Nostr, creamos un modelo donde el crecimiento de la plataforma directamente financia su propio desarrollo.

Los operadores obtienen una herramienta más robusta, los usuarios mantienen sus costos bajos, y el proyecto asegura recursos para continuar innovando. Es un ejemplo concreto de cómo la tecnología puede alinear incentivos para crear valor sostenible en el ecosistema Bitcoin.

## Más información

- **Documentación técnica**: [https://github.com/MostroP2P/mostro/blob/main/docs/DEV_FEE.md](https://github.com/MostroP2P/mostro/blob/main/docs/DEV_FEE.md)  

¡La sostenibilidad del desarrollo ya no es una preocupación, sino una característica automática del sistema!