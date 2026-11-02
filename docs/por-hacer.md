# Por hacer

Lo que queda, separado en lo que hay que hacer para que funcione lo que ya
está, lo que solo puedo escribir yo y lo que se puede añadir. Al día del 13 de
octubre de 2026, con 210 fichas.

## Hecho desde la lista anterior

Privacidad en tres niveles (`draft`, `hidden` entero o por campos, y la carpeta
`privado/`), grupos hechos a mano (el anime se resolvió así: *Anime y manga*),
el anuario con `finished_on`, una tarjeta para compartir cada ficha, comparar
con un fichero, y Vitrine como plantilla en castellano o en inglés
(`scripts/empezar.py`, la web y los scripts en los dos idiomas).

El 17 de octubre: cuántas veces has terminado algo (`times`), spoilers
plegados, el color de la portada en su ficha, las salas por décadas, «de la misma historia» (`based_on`, `follows`,
`soundtrack`, con `scripts/enlazar.py` desde Wikidata), y *Sorpréndeme*, de
esta vitrina o de otra.

Después, el mismo día: la «cartela» pasó a llamarse opinión; editar una ficha
desde la web (el Issue **Editar pieza**); `scripts/cuando.py`, que pone
`finished_on` y `started_on` de Letterboxd, Steam, Goodreads, ListenBrainz o
Spotify (43 juegos ya tienen su mes de empezado y 36 películas su día); y la constelación en tres
niveles (salas, géneros, obras) con flechas para lo de la misma historia.

El 2 de noviembre: la página **Repasar** (`/repasar/`), que va una a una por
lo que no tiene opinión o nota y abre el Issue de editar ya relleno (la nota
del Issue pasó a ser texto, para que se pueda rellenar desde la dirección); las
tarjetas para compartir en JPEG (la web bajó de 142 a 31 MB) y su caché
guardada entre despliegues; la Action **Empezar mi vitrina**, para hacerse una
sin terminal; la Action **Importar cada noche**; los estados vacíos de una
vitrina recién empezada; los amigos a un toque en Comparar; una captura en el
README, el repo marcado como plantilla y **«Me llegó por»** (`via`: quién te
la recomendó, con una página por persona). De paso: las pruebas de editar
fallaban en cualquier vitrina en inglés (y con ellas el despliegue), y el
`--dry-run` de importar contaba como nuevo lo que ya estaba. El Issue de alta
está probado de verdad (#1, con una que ya estaba).

## Para que funcione lo que ya está

- **Subir `main`.** Lo de arriba (Repasar, la nota como texto en el Issue, las
  dos Actions nuevas) no existe en GitHub hasta entonces.
- **Las cuentas para la importación de cada noche**, como secrets del repo:
  `gh secret set LETTERBOXD` y `gh secret set STEAM` (y `LISTENBRAINZ`,
  `GOODREADS` si los usas). Y, para que pueda abrir el PR, *Settings → Actions
  → General → Allow GitHub Actions to create and approve pull requests*.

- **Goodreads o ListenBrainz**, si los usas: su usuario en
  `vitrine.local.json` y `cuando.py` saca las fechas de libros y discos.
  Letterboxd y Steam ya están. El RSS de Letterboxd solo trae las últimas ~50
  películas: lo que se vio antes va a mano o con el export.

- **Comprobar la web publicada**: que las direcciones viejas abren
  (`juegos/golf-it!`, `tags/action`, `index.xml`), que al pegar el enlace de una
  ficha en un chat sale su tarjeta, y que instalarla como app saca *Vitrina* en
  el menú de Compartir.

- **Darla a conocer**, cuando haya opiniones: r/ObsidianMD, r/selfhosted y un
  *Show HN*. El gancho es que ninguna fuente pide clave ni cuenta y que se
  publica gratis en GitHub Pages.

## Lo que solo puedo escribir yo

- **Las opiniones.** Hay cinco y cuatro son el texto de prueba (*Hollow Knight
  Silksong*, *Eternal Sunshine of the Spotless Mind*, *In Rainbows*, *Breaking
  Bad*). En la portada y en las tarjetas se ven mucho. `/repasar/` las pide una
  a una desde el móvil, y `scripts/repasar.py` desde la terminal.
- **Las notas.** 43 de 240 tienen; `/repasar/`, pestaña *Sin nota*. Sin nota, el orden «por aprecio» y las
  cifras se quedan cojos.
- **Los estados.** Casi todo es `finished`; no hay nada `in-progress`, así que
  esa parte de los filtros está vacía.
- **Las fechas de terminado.** Las películas ya las tienen (Letterboxd) y los
  juegos tienen cuándo los empezaste (Steam). Las series, los libros y cuándo
  terminaste cada juego van a mano; con el año basta.
- **La presentación de la portada**, el primer párrafo de `content/index.md`.
  El borrador: «Una vitrina de lo que juego, veo, leo y escucho. No todo lo que
  pasa por mis manos: lo que se queda. Cada pieza lleva su opinión con lo que
  me dejó, y juntas dicen de mí más de lo que yo sabría contar.»
- **Más grupos**, si quieres: el de *Anime y manga* es el ejemplo.
- **Lo que no encuentran los scripts.** *Fortnite* no tiene portada (en
  Wikipedia solo está el logo) y quedan discos sin géneros: *DISOBEY VOL. II*,
  *Million Dollar Baby*, *Konbanwa* y *Wild Heart*. A mano, o se quedan así:
  antes vacío que equivocado.

## Borradores

Lo que se hizo y se sacó de la web, guardado entero por si vuelve.

- **El reproductor** (rama `borrador/reproductor`). El disco de Spotify
  desplegado en la ficha y el tráiler de YouTube encima, que no se cargaban
  hasta pulsar, con `spotify` y `trailer` en 100 fichas y `enlazar.py`
  rellenándolos desde Wikidata. Se quitó el 17 de octubre de 2026: la vitrina
  no tiene por qué cargar otros sitios. La rama lo guarda tal como estaba, y
  revertir el commit que lo quitó de `main` lo trae de vuelta.

## Lo que se puede añadir

De más a menos útil, a mi juicio.

- **Sellos, como los de Passport.** Guardada como idea: es lo más «de
  aplicación» y necesita un criterio antes de código. La forma que encaja con
  la vitrina es que **cada uno haga los suyos**, como los grupos: una nota por
  sello con su condición (`tags: [roguelike]` y 5 piezas, `author:
  FromSoftware`, `year < 1960`, `times >= 3`…) y la web dice cuáles has
  ganado y cuándo (el `added` o `finished_on` de la pieza que lo completó).
  Unos pocos de serie, que se puedan apagar.
- **Bandas sonoras.** Hoy no hay ninguna puesta: Wikidata casi nunca sabe
  cuál es el disco, así que van a mano (`soundtrack: ["[[musica/…]]"]`).
- **Más niveles en la constelación**: entre géneros y obras, los autores; o
  los grupos que haces tú como otra forma de agruparlas.
- **«Me llevó a».** Un enlace de una obra a la siguiente que descubriste por
  ella; la constelación lo dibujaría con flechas.
- **Los docs en inglés.** El README está en los dos idiomas; `docs/scripts.md`
  y `docs/importar.md`, solo en castellano.
- **Más letras para las tarjetas.** Los títulos en japonés bajan su fuente de
  Google Fonts (Noto Sans JP); uno en coreano saldría con cuadros. Habría que
  elegir la Noto de cada alfabeto.
- **Más idiomas.** En la web es copiar el diccionario de `web/src/i18n.ts`. En
  los scripts, además de copiar `mensajes_en.py`, `_()` de `vitrina.py` tendría
  que elegir el catálogo por idioma, que hoy es castellano o inglés; y su
  entrada en `IDIOMAS` de `scripts/empezar.py`.
