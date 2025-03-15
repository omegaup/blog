---
title: Home
layout: hextra-home
sidebar:
  exclude: true
toc: true
---
{{< hextra/hero-headline >}}
  Blog 
  <img class="hx-text-center hx-hidden dark:hx-block" src="/logo/omegaUp-dark.webp" alt="omegaUp blog" width="250">
  <img class="hx-text-center hx-block dark:hx-hidden" src="/logo/omegaUp.webp" alt="omegaUp blog" width="250">
{{< /hextra/hero-headline >}}

{{< callout type="info" emoji=" " >}}
  **Incrementando el talento de Ingeniería de Software en América Latina.**
{{< /callout >}}

<div class="hx-mt-6 hx-mb-6">
{{< hextra/feature-grid >}}
  {{% details title="Para comenzar" %}}
  <a href='/comienza'>omegaUp es una plataforma educativa gratuita que te ayuda a mejorar tus habilidades de programación.</a><br><br>
  &#8226; <a class="hx-text-[color:hsl(var(--primary-hue),100%,50%)] hx-underline hx-underline-offset-2 hx-decoration-from-font" href='/comienza/#crea-tu-cuenta-en-omegaupcomloginhttpsomegaupcomlogin'>Crear una cuenta</a><br>
  &#8226; <a class="hx-text-[color:hsl(var(--primary-hue),100%,50%)] hx-underline hx-underline-offset-2 hx-decoration-from-font" href='/comienza/#completa-tu-perfil-en-mi-perfilhttpsomegaupcomprofile'>Cambiar correo o contraseña</a><br>
  &#8226; <a class="hx-text-[color:hsl(var(--primary-hue),100%,50%)] hx-underline hx-underline-offset-2 hx-decoration-from-font" href='/comienza/#completa-tu-perfil-en-mi-perfilhttpsomegaupcomprofile'>Completar mi perfil</a><br>
  <a class="hx-text-[color:hsl(var(--primary-hue),100%,50%)] hx-underline hx-underline-offset-2 hx-decoration-from-font" href='/comienza'>Ver más</a>
  {{% /details %}}

  {{% details title="Popular" %}}
  <a href='/posts'>Descubre nuestra información actualizada relevante.</a><br><br>
  &#8226; <a class="hx-text-[color:hsl(var(--primary-hue),100%,50%)] hx-underline hx-underline-offset-2 hx-decoration-from-font" href='/posts/introduccion-a-omegaup-parte-0/'>¿Cómo resolver problemas?</a><br>
  &#8226; <a class="hx-text-[color:hsl(var(--primary-hue),100%,50%)] hx-underline hx-underline-offset-2 hx-decoration-from-font" href='/posts/codigo-de-conducta-en-omegaup/'>Código de conducta.</a><br>
  &#8226; <a class="hx-text-[color:hsl(var(--primary-hue),100%,50%)] hx-underline hx-underline-offset-2 hx-decoration-from-font" href='/posts/el-nuevo-buscador-de-problemas-de-omegaup/'>¿Cómo buscar problemas?</a><br>
  &#8226; <a class="hx-text-[color:hsl(var(--primary-hue),100%,50%)] hx-underline hx-underline-offset-2 hx-decoration-from-font" href='/posts/concursos-con-subtareas/#c%C3%B3mo-crear-un-concurso-con-la-modalidad-de-subtareas'>¿cómo crear concursos?</a><br>
  &#8226; <a class="hx-text-[color:hsl(var(--primary-hue),100%,50%)] hx-underline hx-underline-offset-2 hx-decoration-from-font" href='/posts/reglas-del-coder-del-mes/'>Reglas del coder del mes.</a>
  {{% /details %}}

  {{% details title="Lo más nuevo" %}}
  <a href='/posts'>Publicamos contenido para difundir habilidades de programación.</a><br><br>
  &#8226; <a class="hx-text-[color:hsl(var(--primary-hue),100%,50%)] hx-underline hx-underline-offset-2 hx-decoration-from-font" href='/posts/soluciones-de-problemas-en-omegaup/'>Soluciones a problemas en omegaUp</a><br>
  &#8226; <a class="hx-text-[color:hsl(var(--primary-hue),100%,50%)] hx-underline hx-underline-offset-2 hx-decoration-from-font" href='/posts/concursos-con-subtareas/#c%C3%B3mo-crear-un-concurso-con-la-modalidad-de-subtareas'>Concursos con subtareas</a><br>
  &#8226; <a class="hx-text-[color:hsl(var(--primary-hue),100%,50%)] hx-underline hx-underline-offset-2 hx-decoration-from-font" href='https://omegaup.com/rank/authors/'>Ranking de contribuidores</a><br>
  <a class="hx-text-[color:hsl(var(--primary-hue),100%,50%)] hx-underline hx-underline-offset-2 hx-decoration-from-font" href='/posts'>Ver más</a>
  {{% /details %}}

{{< /hextra/feature-grid >}}
</div>

{{ define "main" }}
  {{ .Content }}
  {{ partial "recent-posts.html" . }}
{{ end }}