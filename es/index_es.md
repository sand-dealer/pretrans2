---
layout: correo
title: Métricas de rendimiento centradas en el usuario
authors:
  - felipewalton
date: '2019-11-08'
description: |2

  Las métricas de rendimiento centradas en el usuario son una herramienta fundamental para comprender y

  mejorando la experiencia de su sitio de una manera que beneficie

  usuarios
tags:
  - actuación
  - métrica
---

Todos hemos escuchado lo importante que es el rendimiento. Pero cuando hablamos de rendimiento y de hacer que los sitios web sean "rápidos", ¿a qué nos referimos específicamente?

La verdad es que el rendimiento es relativo:

- Un sitio puede ser rápido para un usuario (en una red rápida con un dispositivo potente) pero lento para otro usuario (en una red lenta con un dispositivo de gama baja).
- Dos sitios pueden terminar de cargarse exactamente en la misma cantidad de tiempo, pero uno puede *parecer* que carga más rápido (si carga el contenido progresivamente en lugar de esperar hasta el final para mostrar algo).
- Puede *parecer que* un sitio se carga rápidamente, pero luego responde lentamente (o no responde en absoluto) a la interacción del usuario.

Entonces, cuando se habla de desempeño, es importante ser preciso y referirse al desempeño en términos de criterios objetivos que se pueden medir cuantitativamente. Estos criterios se conocen como *métricas* .

Pero el hecho de que una métrica se base en criterios objetivos y se pueda medir cuantitativamente no significa necesariamente que esas medidas sean útiles.

## Definición de métricas

Históricamente, el rendimiento web se ha medido con el evento <code>[load](https://developer.mozilla.org/en-US/docs/Web/API/Window/load_event)</code> . Sin embargo, aunque <code>load</code> es un momento bien definido en el ciclo de vida de una página, ese momento no se corresponde necesariamente con nada que le interese al usuario.

Por ejemplo, un servidor podría responder con una página mínima que se "carga" inmediatamente, pero luego difiere la obtención de contenido y la visualización de cualquier cosa en la página hasta varios segundos después de que se activa el evento de `load` . Si bien una página de este tipo técnicamente podría tener un tiempo de carga rápido, ese tiempo no se correspondería con la forma en que un usuario realmente experimenta la carga de la página.

En los últimos años, los miembros del equipo de Chrome, en colaboración con el [Grupo de trabajo de rendimiento web de W3C](https://www.w3.org/webperf/) , han estado trabajando para estandarizar un conjunto de nuevas API y métricas que miden con mayor precisión cómo los usuarios experimentan el rendimiento de una página web.

Para ayudar a garantizar que las métricas sean relevantes para los usuarios, las enmarcamos en torno a algunas preguntas clave:

<table id="questions">
  <tr>
    <td><strong>¿Está sucediendo?</strong></td>
    <td>¿La navegación se inició con éxito? ¿Ha respondido el servidor?</td>
  </tr>
  <tr>
    <td><strong>¿Es útil?</strong></td>
    <td>¿Se ha renderizado suficiente contenido para que los usuarios puedan interactuar con él?</td>
  </tr>
  <tr>
    <td><strong>¿Es usable?</strong></td>
    <td>¿Pueden los usuarios interactuar con la página o está ocupada?</td>
  </tr>
  <tr>
    <td><strong>¿Es delicioso?</strong></td>
    <td>¿Son las interacciones fluidas y naturales, libres de retrasos y bloqueos?</td>
  </tr>
</table>

## Cómo se miden las métricas

Las métricas de rendimiento generalmente se miden de una de dos maneras:

- **En el laboratorio:** uso de herramientas para simular la carga de una página en un entorno uniforme y controlado
- **En el campo** : en usuarios reales que realmente cargan e interactúan con la página

Ninguna de estas opciones es necesariamente mejor o peor que la otra; de hecho, generalmente desea usar ambas para garantizar un buen rendimiento.

### En el laboratorio

Probar el rendimiento en el laboratorio es esencial cuando se desarrollan nuevas funciones. Antes de que las funciones se publiquen en producción, es imposible medir sus características de rendimiento en usuarios reales, por lo que probarlas en el laboratorio antes de que se lance la función es la mejor manera de evitar regresiones en el rendimiento.

### En el campo

Por otro lado, si bien las pruebas en el laboratorio son un indicador razonable del rendimiento, no necesariamente reflejan cómo todos los usuarios experimentan su sitio en la naturaleza.

El rendimiento de un sitio puede variar drásticamente según las capacidades del dispositivo del usuario y las condiciones de su red. También puede variar según si (o cómo) un usuario está interactuando con la página.

Además, las cargas de página pueden no ser deterministas. Por ejemplo, los sitios que cargan contenido o anuncios personalizados pueden experimentar características de rendimiento muy diferentes de un usuario a otro. Una prueba de laboratorio no captará esas diferencias.

La única forma de saber realmente cómo funciona su sitio para sus usuarios es medir realmente su rendimiento a medida que esos usuarios lo cargan e interactúan con él. Este tipo de medición se conoce comúnmente como [monitoreo de usuario real](https://en.wikipedia.org/wiki/Real_user_monitoring) , o RUM para abreviar.

## Tipos de métricas

Hay varios otros tipos de métricas que son relevantes para la forma en que los usuarios perciben el rendimiento.

- **Velocidad de carga percibida:** qué tan rápido puede cargar una página y mostrar todos sus elementos visuales en la pantalla.
- **Capacidad de respuesta de carga:** qué tan rápido una página puede cargar y ejecutar cualquier código JavaScript requerido para que los componentes respondan rápidamente a la interacción del usuario
- **Capacidad de respuesta en tiempo de ejecución:** después de cargar la página, qué tan rápido puede responder la página a la interacción del usuario.
- **Estabilidad visual:** ¿los elementos de la página cambian de formas que los usuarios no esperan e interfieren potencialmente con sus interacciones?
- **Suavidad:** ¿las transiciones y las animaciones se procesan a una velocidad de fotogramas constante y fluyen con fluidez de un estado al siguiente?

Teniendo en cuenta todos los tipos de métricas de rendimiento anteriores, es de esperar que quede claro que ninguna métrica es suficiente para capturar todas las características de rendimiento de una página. [Actualizado]

## Nuevo texto de encabezado agregado [Nuevo]

[Nuevo] Otro siguiente agregado en origen. Actuación de la noche. Mundo perfecto y otras palabras aquí se presentan.

## Métricas importantes a medir

- **[Primera pintura con contenido (FCP)](/fcp/) :** mide el tiempo desde que la página comienza a cargarse hasta que cualquier parte del contenido de la página se representa en la pantalla. *( [laboratorio](#in-the-lab) , [campo](#in-the-field) )*
- **[Pintura con contenido más grande (LCP)](/lcp/) :** mide el tiempo desde que la página comienza a cargarse hasta que el bloque de texto o elemento de imagen más grande se representa en la pantalla. *( [laboratorio](#in-the-lab) , [campo](#in-the-field) )*
- **[Retraso en la primera entrada (FID)](/fid/) :** mide el tiempo desde que un usuario interactúa por primera vez con su sitio (es decir, cuando hace clic en un enlace, presiona un botón o usa un control personalizado con JavaScript) hasta el momento en que el navegador es realmente capaz para responder a esa interacción. *( [campo](#in-the-field) )*
- **[Tiempo de interacción (TTI)](/tti/) :** mide el tiempo desde que la página comienza a cargarse hasta que se representa visualmente, sus scripts iniciales (si los hay) se han cargado y es capaz de responder de manera confiable a la entrada del usuario rápidamente. *( [laboratorio](#in-the-lab) )*
- **[Tiempo total de bloqueo (TBT)](/tbt/) :** mide la cantidad total de tiempo entre FCP y TTI donde el subproceso principal estuvo bloqueado durante el tiempo suficiente para evitar la capacidad de respuesta de entrada. *( [laboratorio](#in-the-lab) )*
- **[Cambio de diseño acumulativo (CLS)](/cls/) :** mide la puntuación acumulada de todos los cambios de diseño inesperados que ocurren entre el momento en que la página comienza a cargarse y el [estado del ciclo de vida](https://developers.google.com/web/updates/2018/07/page-lifecycle-api) cambia a oculto. *( [laboratorio](#in-the-lab) , [campo](#in-the-field) )*

Si bien esta lista incluye métricas que miden muchos de los diversos aspectos del rendimiento relevantes para los usuarios, no incluye todo (por ejemplo, la capacidad de respuesta y la fluidez del tiempo de ejecución no están cubiertas actualmente).

En algunos casos, se introducirán nuevas métricas para cubrir las áreas que faltan, pero en otros casos, las mejores métricas son las que se adaptan específicamente a su sitio.

## Métricas personalizadas

Las métricas de rendimiento enumeradas anteriormente son buenas para obtener una comprensión general de las características de rendimiento de la mayoría de los sitios en la web. También son buenos para tener un conjunto común de métricas para que los sitios comparen su rendimiento con el de sus competidores.

Sin embargo, puede haber momentos en que un sitio específico sea único de alguna manera que requiera métricas adicionales para capturar la imagen completa del rendimiento. Por ejemplo, la métrica LCP está diseñada para medir cuándo el contenido principal de una página ha terminado de cargarse, pero puede haber casos en los que el elemento más grande no forme parte del contenido principal de la página y, por lo tanto, LCP puede no ser relevante.

[Nuevo] simplemente agregue otro párrafo con información inútil.

Para abordar estos casos, el Grupo de trabajo de rendimiento web también ha estandarizado las API de nivel inferior que pueden ser útiles para implementar sus propias métricas personalizadas:

- [API de tiempo de usuario](https://w3c.github.io/user-timing/)
- [API de tareas largas](https://w3c.github.io/longtasks/)
- [API de temporización de elementos](https://wicg.github.io/element-timing/)
- [API de temporización de navegación](https://w3c.github.io/navigation-timing/)
- [API de temporización de recursos](https://w3c.github.io/resource-timing/)
- [Temporización del servidor](https://w3c.github.io/server-timing/)

Consulte la guía sobre [métricas personalizadas](/custom-metrics/) para aprender a usar estas API para medir las características de rendimiento específicas de su sitio.
