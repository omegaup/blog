---
title: 'Guía para la Propuesta de Insignias en omegaUp'
author: 'Carlos Córdova'
author_email: 'carlos@omegaup.com'
date: Tue, 08 Oct 2019 14:54:10 +0000
draft: false
tags: ['Documentation', 'Ranking', 'badges', 'Contribuir a omegaUp', 'contribuir-a-omegaup']
---

Tú también puedes proponer nuevas insignias para la plataforma, simplemente debes tomar en cuenta las consideraciones que se detallan a continuación y abrir un issue en nuestro repositorio en Github haciendo clic [aquí](https://github.com/omegaup/omegaup/issues/new?assignees=&labels=&template=propuesta-para-nueva-insignia.md&title=%5BBadge+Proposal%5D+Nombre+de+la+Insignia).

**Consideraciones:**

*   Las insignias en omegaUp son una manera de reconocer logros pequeños pero significativos, conseguidos por los usuarios al usar la plataforma. En dicho sentido, no está permitido proponer insignias _ad-hoc_, cuya posibilidad de ser conseguidas involucre aspectos que van más allá de la habilidad del estudiante o el uso que éste le da a la plataforma. Por ejemplo:
    *   Insignia por haber ganado un concurso en Enero
    *   Insignia por tener un nombre de usuario menor a 5 caracteres

 

*   El nombre de una insignia está limitado a **50 caracteres** y debe ser pensado como una característica y no como una acción del usuario. Por ejemplo, si lo que se desea proponer es una insignia para un usuario que ha enviado feedback sobre un problema, el nombre de dicha insignia debe ser: “Proveedor de Feedback”, en lugar de “Proveer Feedback” o “Haber provisto de Feedback”.

 

*   La descripción de una insignia debe responder a la pregunta: ¿Qué debe haber realizado un usuario para recibir esta insignia?, y debe seguir el siguiente formato: “El usuario realizó \[inserte la acción que realizó\]”.

 

*   Una insignia puede tener un ícono personalizado proporcionado por la persona que la propone o implementa. Los íconos personalizados tienen ciertas restricciones, que son:
    *   Debe ser un archivo .svg
    *   Las dimensiones del ícono son 600x600 píxeles.
    *   El archivo debe tener un peso máximo de 15kB.
    *   El ícono debe mantener siempre la forma de la insignia por defecto, lo único que puede ser ajustado son los colores y el relleno de la misma. Por lo tanto, en caso de ser requerido, el ícono personalizado puede ser creado a partir de una modificación del ícono por defecto, el cual puede ser descargado del [siguiente enlace](https://raw.githubusercontent.com/omegaup/omegaup/master/frontend/badges/default_icon.svg).

 

*   El usuario que propone una insignia puede indicar también cómo debería ser la consulta en la base de datos, para que ésta sea asignada e incluso la prueba unitaria que se puede realizar. De esta manera podrá facilitar el trabajo de la persona que se encargue de implementar la misma.