# keyvon-web

Web mínima y pública de KEYVON, publicada con GitHub Pages en <https://keyvon.es>.
Tiene solo dos páginas: la portada y la política de privacidad. No es la web comercial.

| Página | Fichero | URL |
| --- | --- | --- |
| Portada | `index.html` | https://keyvon.es/ |
| Política de privacidad | `privacidad/index.html` | https://keyvon.es/privacidad/ |
| Estilos (compartidos) | `estilos.css` | |

Este repositorio es **público** (GitHub Pages gratuito lo exige). No debe contener nunca secretos,
datos de `keyvon-prototype` ni datos personales aparte de los que ya trae la política.

## Reglas de la web

- Estática: HTML y CSS escritos a mano. Sin frameworks, sin JavaScript, sin paso de compilación.
- **Cero servicios de terceros**: ni Google Fonts, ni analítica, ni píxeles, ni iconos o scripts de CDN, ni cookies.
  Se usan las fuentes del sistema. Por eso no hay banner de cookies y la política (que no menciona ninguno de
  esos servicios) sigue siendo cierta. Si algún día se añade uno, hay que actualizar antes la política.
- Accesible y legible en móvil. Las tablas de la política pasan a ser tarjetas en pantallas estrechas.
- `CNAME` contiene `keyvon.es`: no borrarlo ni cambiarlo (GitHub Pages lo usa para el dominio propio).
- `.nojekyll` desactiva el procesado Jekyll: se publica el HTML tal cual.

## Política de privacidad: una sola verdad

Desde su publicación, **la fuente oficial de la política es `privacidad/index.html` de este repositorio**.
El fichero `politica_privacidad_keyvon_v1.md` de la carpeta Traspasos queda solo como histórico y ya no se edita.

Para cambiar la política:

1. Edita **solo** `privacidad/index.html`.
2. Actualiza la fecha de la línea «Última actualización» (al final del fichero).
3. Haz un commit propio, solo con ese cambio, cuyo mensaje **empiece por `privacidad:`**
   (por ejemplo: `privacidad: añadir proveedor X al apartado 6`).

Anclas que no deben cambiar (otras plataformas enlazan a ellas):

- `#eliminacion-de-datos`: instrucciones de eliminación de datos (apartado 9). Es la URL que pide Meta:
  https://keyvon.es/privacidad/#eliminacion-de-datos
- `#responsable`, `#que-es-keyvon`, `#datos-que-tratamos`, `#finalidades`, `#inteligencia-artificial`,
  `#destinatarios`, `#transferencias`, `#conservacion`, `#derechos`, `#seguridad-menores-cambios`
  (apartados 1 a 10).

## Dominio y DNS (GoDaddy)

Los registros DNS se ponen a mano en GoDaddy (ver la lista exacta entregada aparte). Valores según la
[documentación de GitHub Pages](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site):

- `@` → 4 registros A: `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
- `@` → 4 registros AAAA (opcionales): `2606:50c0:8000::153`, `2606:50c0:8001::153`, `2606:50c0:8002::153`, `2606:50c0:8003::153`
- `www` → CNAME a `<usuario-de-github>.github.io` (sin el nombre del repositorio)

No tocar los registros de correo (MX, TXT de Microsoft 365) de keyvon.es.

### Comprobar el HTTPS

GitHub emite el certificado solo cuando los DNS están bien puestos (puede tardar hasta 24 horas).

1. En GitHub: repositorio → **Settings → Pages**. Mientras el certificado no está listo, el aviso dice que
   está pendiente y la casilla **Enforce HTTPS** aparece desactivada. Cuando se pueda, márcala.
2. Comprobar los DNS desde la terminal: `dig +short A keyvon.es` (deben salir las 4 IP de GitHub) y
   `dig +short CNAME www.keyvon.es`.
3. Comprobar el certificado: `curl -sI https://keyvon.es/ | head -1` debe responder `HTTP/2 200` sin error de
   certificado, y `curl -sI http://keyvon.es/ | head -3` debe redirigir (301) a `https://`.
4. Abrir https://keyvon.es/ y https://keyvon.es/privacidad/ en el navegador y comprobar que aparece el candado.

## Pendiente (fuera de alcance de este encargo)

- **Aviso legal**: la LSSI exige nombre, NIF, domicilio y correo. Falta decidir el domicilio.
- **Web comercial de KEYVON**: proyecto aparte, con maquetas.
- **Cambios en `keyvon-prototype`**: por ejemplo, el correo `contacto@keyvon.ai` de `geocodingService.js`
  va a otro encargo.
