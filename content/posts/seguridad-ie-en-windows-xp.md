---
title: 'Seguridad: IE en Windows XP'
author: 'lhchavez'
author_email: 'lhchavez@omegaup.com'
date: Sun, 05 Jan 2014 20:37:08 +0000
draft: false
tags: ['News', 'Internals']
---

Debido a un reciente cambio para mejorar la seguridad de la conexión a omegaUp, hemos decidido dejar de soportar oficialmente IE en Windows XP, a pesar de que sabemos que aún sigue siendo el segundo sistema operativo más común a nivel mundial\[1\]. Si aún están obligados a usar Windows XP, por favor utilicen algún navegador moderno (Chrome, Firefox u Opera) o alguna versión [portátil](http://portableapps.com/apps/internet).

Para los interesados, el cambio consistió en hacer un par de optimizaciones para nginx\[2\], para reducir el tiempo de espera al primer byte, y actualizar la configuración de TLS: se quitaron SSLv2 y SSLv3 (que ya se consideran inseguros), se agregaron TLSv1.1 y TLSv1.2, se eliminó RC4 como algoritmo de cifrado, y ahora se prefiere ECDHE como algoritmo de intercambio de llaves para proveer Perfect Forward Secrecy\[3\].

Referencias
-----------

1.  Reporte NetMarketShare, Enero 2014    
2.  [Optimizing NGINX TLS Time To First Byte (TTFB)](http://www.igvita.com/2013/12/16/optimizing-nginx-tls-time-to-first-byte/) - igvita.com
3.  [Perfect Forward Secrecy](http://es.wikipedia.org/wiki/Perfect_forward_secrecy) - Wikipedia