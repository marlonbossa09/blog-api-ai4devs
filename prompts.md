# Prompts

Aquí van **todos los prompts que lanzaste** para hacer el ejercicio, en el orden en que los
lanzaste, con el modelo y la herramienta de cada uno.

Esto no es papeleo. Lo que se revisa es **cómo pediste las cosas**, no solo lo que salió: un
resultado flojo con un prompt bueno y un resultado flojo con un prompt vago necesitan feedback
distinto, y sin este archivo no se distinguen.

## Cómo rellenarlo

- Un apartado `## Prompt N` por cada prompt.
- **Pega el prompt tal cual lo lanzaste**, dentro del bloque de código, aunque ocupe diez líneas
  y aunque tenga faltas. No lo reescribas para que quede bien: el que arreglaste mentalmente
  después no es el que lanzaste.
- Incluye también los que **no funcionaron**. Suelen ser los más útiles de leer.
- `Modelo` y `Herramienta` en todos. Si cambiaste de una a otra a mitad, se nota aquí.

---

**Nota de transparencia:** están todos los prompts de la conversación de trabajo, copiados tal cual. Los prompts 1 a 5 y 7 los escribí yo (Edwin Quintana); el 6, el 8 y el 9 los lanzó Claude Code por su cuenta (una consulta de documentación y las dos sesiones independientes del experimento). No tengo constancia de ningún otro prompt anterior a esta conversación. El nivel de esfuerzo (effort) del modelo no consta y no lo indico.

---

## Prompt 1

**Modelo:** Claude Sonnet 5.5 (`claude-sonnet-5-5`)
**Herramienta:** Claude Code (extensión de VS Code)

```
Vamos a realizar la actividad del Módulo 7 sobre gobierno de agentes en múltiples repositorios.

Trabajaremos como Edwin Quintana (EQ), utilizando tres repositorios independientes: blog-ai, blog-api y blog-web.

Antes de realizar cualquier modificación, necesito que:

1. Verifiques si Docker, Ollama, Python y Git están instalados y funcionando.
2. Compruebes si ya existen los tres repositorios en el directorio de trabajo o en carpetas hermanas.
3. Identifiques la rama actual y los remotos configurados de cada repositorio existente.
4. Compruebes si los repositorios tienen cambios locales sin guardar.
5. Verifiques si están disponibles los puertos 8402, 3402 y 5402.
6. Identifiques cualquier dependencia o problema que pueda impedir ejecutar la actividad.

Restricciones:
- No modifiques archivos.
- No instales dependencias.
- No crees ramas todavía.
- No realices commits, push ni Pull Requests.
- No descartes cambios existentes.
- No modifiques repositorios ajenos a esta actividad.
- No ejecutes acciones destructivas.

Al finalizar, presenta un diagnóstico organizado con el estado de cada herramienta, repositorio y servicio.

Indica qué está listo, qué falta y cuál debe ser el siguiente paso.

No avances a la implementación sin mi autorización.
```

**Qué salió:** diagnóstico completo; detectó Docker apagado, Python 3.14 en vez de 3.13 y el puerto 5433 ocupado.

## Prompt 2

**Modelo:** Claude Sonnet 5.5 (`claude-sonnet-5-5`)
**Herramienta:** Claude Code (extensión de VS Code)

```
Continuemos con la preparación del entorno para la actividad del Módulo 7, trabajando como Edwin Quintana (EQ).

Ya realizaste el diagnóstico inicial y autorizo preparar los tres repositorios existentes.

Decisiones:

1. Docker:
- Intenta iniciar Docker Desktop.
- Verifica que el motor de contenedores responda correctamente.
- No elimines contenedores, volúmenes ni imágenes existentes.

2. Python:
- Instala Python 3.13 en paralelo con Python 3.14, si es necesario.
- No desinstales ni reemplaces Python 3.14.
- Configura blog-ai para utilizar Python 3.13 en su entorno virtual.
- No cambies las dependencias del proyecto ni utilices la rama fix/psycopg-python-314.

3. Repositorios:
- Conserva los tres clones existentes.
- Renombra únicamente sus carpetas para que queden:
  - blog-ai
  - blog-api
  - blog-web
- No modifiques los repositorios ajenos a esta actividad.
- No ejecutes operaciones Git desde el repositorio superior C:/Users/COMPUMAX.

4. Git:
- Configura upstream en cada repositorio apuntando al repositorio oficial correspondiente de LIDR-academy.
- Ejecuta git fetch upstream.
- Verifica que exista upstream/s7/start.
- Crea la rama local s7/start desde upstream/s7/start en los tres repositorios.
- No realices merges ni rebases.
- No crees todavía la rama frontera-eq.
- Configura git user.name como "Edwin Quintana" únicamente en estos tres repositorios.
- Conserva provisionalmente el user.email existente; informa su valor para validarlo antes de cualquier commit.

5. Ollama:
- Comprueba qué modelos exige realmente la configuración de blog-ai.
- Descarga únicamente los modelos faltantes necesarios para ejecutar la actividad.
- No elimines modelos existentes.

6. Validación:
- Ejecuta make check en los tres repositorios desde un entorno compatible con los Makefile.
- Comprueba las versiones, remotos, ramas y estado Git.
- Comprueba que Docker y Ollama respondan.

Restricciones:
- No modifiques código fuente.
- No alteres archivos de dependencias.
- No ejecutes todavía make setup ni make up.
- No realices commits, push ni Pull Requests.
- No descartes cambios locales.
- Si encuentras un conflicto o un error que exija cambiar el enfoque, detente y explícame las alternativas antes de continuar.

Al finalizar, entrega una tabla con el estado de cada repositorio y herramienta, las acciones realizadas, los errores encontrados y los próximos pasos.

No avances a la siguiente fase sin mi autorización.
```

**Qué salió:** Docker, Python 3.13 y el modelo de Ollama quedaron listos. No pudo renombrar las carpetas (acceso denegado) y el upstream `LIDR-academy` no existe (el padre real de los forks es `LIDR-academy-temp`), así que se detuvo y propuso alternativas.

## Prompt 3

**Modelo:** Claude Sonnet 5.5 (`claude-sonnet-5-5`)
**Herramienta:** Claude Code (extensión de VS Code)

```
Continuemos con la preparación del entorno para el Módulo 7, trabajando como Edwin Quintana (EQ).

Revisé tu diagnóstico y autorizo continuar bajo las siguientes decisiones.

OBJETIVO:
Preparar los repositorios blog-ai, blog-api y blog-web para ejecutar la actividad desde un entorno compatible, sin alterar su código fuente ni afectar proyectos ajenos.

1. REPOSITORIOS Y DIRECTORIOS

Utilizaremos la estructura:

C:\dev\modulo7
  blog-ai
  blog-api
  blog-web\

Antes de mover los repositorios:
- Comprueba si existen archivos o proyectos en las rutas de destino.
- No sobrescribas ninguna carpeta.
- Comprueba si VS Code u otro proceso mantiene bloqueados los directorios.
- No cierres forzosamente procesos ni finalices sesiones.
- Si las carpetas están bloqueadas, informa qué aplicación las utiliza y detente para que pueda liberar el bloqueo.

Cuando las rutas estén disponibles:
- Mueve los tres repositorios existentes.
- No vuelvas a clonarlos.
- Conserva sus respectivos directorios .git.
- Verifica que el historial Git y los remotos sigan intactos.

2. CONFIGURACIÓN DE UPSTREAM

Corrige upstream para apuntar a los repositorios originales identificados:

- LIDR-academy-temp/blog-ai-ai4devs
- LIDR-academy-temp/blog-api-ai4devs
- LIDR-academy-temp/blog-web-ai4devs

Después:
- Ejecuta git fetch upstream.
- Verifica que exista upstream/s7/start.
- Comprueba que no haya cambios locales.
- Crea una rama local s7/start desde upstream/s7/start en cada repositorio.
- No hagas merge ni rebase.
- No crees todavía frontera-eq.

3. PYTHON Y MAKEFILE

Python 3.13.17 ya está instalado.

Necesito que determines cómo ejecutar correctamente los Makefile en Windows sin modificar los archivos versionados.

Comprueba:
- Si make check funciona desde la nueva ruta.
- Si el problema del comando python3.13 persiste.
- Si las rutas .venv/bin son incompatibles con el entorno actual.
- Si es posible resolverlo con un entorno compatible o mediante configuración local.

No modifiques Makefile, archivos de dependencias ni código fuente.

Si es necesario utilizar WSL, propón los cambios mínimos antes de ejecutarlos.

4. PUERTO POSTGRESQL

El puerto 5433 está ocupado por PostgreSQL de Windows.

- No detengas ese servicio.
- No elimines bases de datos.
- Comprueba si el puerto 5434 está libre.
- Analiza si Docker Compose permite cambiar el puerto publicado mediante configuración local sin modificar archivos versionados.
- No realices todavía el cambio ni levantes nuevos contenedores.

5. IDENTIDAD GIT

Conserva:
user.name = Edwin Quintana

Mantén provisionalmente el correo existente.

No realices commits hasta que confirmemos el correo adecuado.

6. VALIDACIONES

Al finalizar, informa:
- Ruta definitiva de cada repositorio.
- Rama activa.
- Configuración de origin y upstream.
- Resultado de make check.
- Compatibilidad de Python 3.13.
- Estado de Docker y Ollama.
- Disponibilidad de puertos.
- Bloqueos pendientes.

RESTRICCIONES:
- No modificar código fuente.
- No modificar archivos versionados.
- No realizar commits ni push.
- No abrir Pull Requests.
- No alterar otros proyectos.
- No eliminar carpetas, contenedores ni bases de datos.
- No ejecutar todavía make setup ni make up.
- Si existe algún bloqueo que no pueda resolverse con seguridad, detente e informa.

Trabaja únicamente sobre los tres repositorios de la actividad y presenta un diagnóstico final antes de continuar.
```

**Qué salió:** no se pudo mover: las carpetas seguían bloqueadas por un proceso que no se identificó (sospecha: VS Code). Sí se corrigió el upstream, se creó `s7/start` y se analizaron Makefile y puerto 5434. Cambié de decisión en el prompt 4.

## Prompt 4

**Modelo:** Claude Sonnet 5.5 (`claude-sonnet-5-5`)
**Herramienta:** Claude Code (extensión de VS Code)

```
Continuemos con la Actividad del Módulo 7, trabajando como Edwin Quintana (EQ).

He decidido que NO vamos a mover ni renombrar los repositorios.

La ubicación definitiva es:

C:\Users\COMPUMAX\Documents\PROYECTOS SOFTCOMPUTO\PROYECTOS\CURSO LIDR\Modulo 7

Los repositorios deben permanecer en sus carpetas actuales:
- blog-ai-ai4devs
- blog-api-ai4devs
- blog-web-ai4devs

No quiero crear C:\dev\modulo7 ni reorganizar mis proyectos.

## 1. Estado ya confirmado

- Docker funciona.
- Python 3.13.17 está instalado.
- Ollama funciona y tiene los modelos necesarios.
- Node, Git y make están instalados.
- Los tres repositorios están en s7/start.
- Los remotos upstream están configurados correctamente.
- Los tres repositorios están limpios.
- El puerto 5433 está ocupado por PostgreSQL de Windows.
- El puerto 5434 está libre.

No repitas instalaciones ni configuraciones ya realizadas.

## 2. Compatibilidad de los Makefile

Analiza cómo ejecutar los tres proyectos desde sus ubicaciones actuales, considerando:

- Las rutas contienen espacios.
- Las carpetas conservan el sufijo -ai4devs.
- Python 3.13 se invoca con py -3.13.
- Los entornos virtuales de Windows utilizan .venv/Scripts.

Prefiero utilizar variables de entorno, comandos equivalentes o scripts auxiliares externos antes que modificar los Makefile.

Si es necesario omitir make check o ejecutar sus comprobaciones manualmente, documenta cómo se verificó cada condición.

No quiero modificar código fuente ni archivos versionados únicamente para adaptar los proyectos a mi equipo.

## 3. PostgreSQL

Utilizaremos el puerto 5434.

- Prepara un override de Docker Compose fuera de los repositorios.
- Verifica que sustituya el puerto 5433, sin publicarlo adicionalmente.
- No detengas PostgreSQL 18 de Windows.
- No alteres contenedores ni bases de datos de otros proyectos.
- Configura la conexión de blog-ai mediante archivos locales ignorados por Git.
- No muestres contraseñas ni secretos.

## 4. Instalación y arranque

Autorizo ejecutar la instalación de dependencias y levantar los tres servicios, siempre que previamente compruebes que los comandos no modificarán archivos versionados ni afectarán otros proyectos.

Respeta el orden:
1. blog-ai — puerto 8402.
2. blog-api — puerto 3402.
3. blog-web — puerto 5402.

Después verifica:
- Salud de blog-ai y conectividad con Ollama.
- Salud de blog-api y comunicación con blog-ai.
- Consulta de posts desde blog-api.
- Acceso a blog-web desde el navegador.
- Indexado mediante POST /indexar.
- Que el indexado procese una cantidad mayor que cero.

No des por exitoso un servicio solo porque su proceso está iniciado. Comprueba su funcionamiento real.

Si aparece un error que requiere modificar código fuente, dependencias versionadas o infraestructura compartida, detente y explica el problema antes de continuar.

## 5. Gobierno de agentes

Cuando los servicios funcionen, inspecciona blog-api y blog-ai para identificar:
- CLAUDE.md o AGENTS.md.
- Hooks o comprobaciones automáticas.
- Comandos, atajos o instrucciones propias del agente.

Esta inspección es únicamente de lectura.

No implementes todavía la regla de la práctica.

## 6. Git y entregables

- Mantén s7/start en los tres repositorios.
- No crees todavía frontera-eq.
- No realices commits ni push.
- No abras Pull Requests.
- Mantén user.name como Edwin Quintana.
- Deja pendiente la confirmación del correo antes del primer commit.
- Conserva los prompts originales para documentarlos posteriormente en prompts.md.

## 7. Resultado esperado

Entrega un informe con:

1. Estado de cada servicio.
2. Comandos utilizados y adaptaciones necesarias en Windows.
3. Evidencias de las pruebas de salud.
4. Resultado del indexado.
5. Estado Git de los tres repositorios.
6. Mecanismos de gobierno de agentes encontrados.
7. Problemas pendientes, si existen.

El objetivo es dejar el entorno funcional y listo para desarrollar la práctica del Módulo 7, sin mover repositorios ni realizar cambios innecesarios.

Detente después de entregar el informe. No avances todavía a implementar la regla entre repositorios.
```

**Qué salió:** los tres servicios quedaron funcionando (indexado de 8 posts y 43 fragmentos) sin mover carpetas. Un comando (`node ace generate:key`) alteró los saltos de línea de `.env.example` y hubo que restaurarlo. No hay `CLAUDE.md`, `AGENTS.md` ni hooks en los repos.

## Prompt 5

**Modelo:** Claude Sonnet 5.5 (`claude-sonnet-5-5`)
**Herramienta:** Claude Code (extensión de VS Code)

```
Continuemos con la práctica principal del Módulo 7, trabajando como Edwin Quintana (EQ).

El entorno ya está preparado:
- blog-ai funciona en el puerto 8402.
- blog-api funciona en el puerto 3402.
- blog-web funciona en el puerto 5402.
- PostgreSQL funciona en el puerto 5434.
- Los tres repositorios están limpios y en s7/start.

OBJETIVO:
Comprobar si una regla de proceso configurada desde blog-api se sigue cumpliendo cuando el agente trabaja desde blog-ai.

REGLA:
"Toda función nueva debe incluir inmediatamente encima un comentario que describa qué devuelve cuando no encuentra resultados".

FASE 1: PREPARACIÓN

1. Trabaja desde el repositorio blog-api-ai4devs, en su ubicación actual.

2. Verifica:
- Rama actual.
- Estado Git.
- Existencia de prompts.md.
- Ausencia o presencia de instrucciones activas del agente.

3. Crea únicamente en blog-api la rama:

frontera-eq

Partiendo de s7/start.

4. Propón un mecanismo local para que Claude Code siga la regla cuando trabaje desde blog-api.

5. Explica dónde se cargaría la instrucción, cuál sería su alcance y cómo podríamos comprobar su cumplimiento.

6. Identifica una modificación de prueba mínima, reversible y no relacionada con la lógica crítica del producto que permita observar la regla tanto desde blog-api como desde blog-ai.

RESTRICCIONES:
- No modifiques todavía código fuente.
- No crees instrucciones en blog-ai.
- No instales hooks globales.
- No cambies configuraciones globales de Claude.
- No hagas commits ni push.
- No abras Pull Requests.
- No escribas todavía las dos frases definitivas de docs/frontera.md.
- No inventes resultados.
- No modifiques blog-web.
- Conserva los prompts originales para documentarlos.

Entrega:
1. Confirmación de la rama frontera-eq.
2. Mecanismo propuesto para aplicar la regla.
3. Alcance esperado de ese mecanismo.
4. Prueba mínima propuesta en ambos repositorios.
5. Archivos que sería necesario modificar.
6. Riesgos y cómo revertir la prueba.

Detente antes de implementar el mecanismo o realizar cambios en el código.
```

**Qué salió:** creó `frontera-eq` en blog-api y propuso `CLAUDE.local.md` con una prueba de dos funciones puras en un archivo nuevo. Predijo, según la documentación, que la regla no se cargaría desde blog-ai.

## Prompt 6

**Modelo:** Claude Sonnet 5.5 (`claude-sonnet-5-5`), lanzado por Claude Code como subagente (`claude-code-guide`) durante la respuesta al prompt 5
**Herramienta:** Claude Code (extensión de VS Code)

```
Necesito respuestas precisas y verificadas en la documentación oficial actual de Claude Code (no de memoria) sobre cómo se cargan las instrucciones del proyecto. Contexto: tengo dos repositorios hermanos independientes (carpetas `blog-api` y `blog-ai`, cada una su propio repo git) dentro de una carpeta común sin git propio. Quiero saber si una regla puesta en blog-api se aplica cuando abro la sesión de Claude Code desde blog-ai. Responde cada punto con cita/enlace a la doc y marca claramente lo que NO aparezca en la documentación:

1. Qué archivos CLAUDE.md se cargan al arrancar `claude` en un directorio X: ¿el de X, los de TODOS los directorios padre hasta la raíz, los de subdirectorios (¿bajo demanda cuando se leen archivos allí?), y se cargan los de carpetas hermanas? ¿Cambia algo si X es la raíz de un repo git y el padre no lo es?
2. `CLAUDE.local.md`: ¿sigue soportado? ¿se recomienda añadirlo a .gitignore? Alternativa de ocultarlo con `.git/info/exclude`.
3. `.claude/settings.json` y `.claude/settings.local.json` de proyecto: ¿en qué directorio deben estar y se aplican solo cuando la sesión arranca en ese proyecto? ¿Se heredan de directorios padre? ¿Se puede definir hooks ahí (PostToolUse con matcher Edit|Write|MultiEdit)?
4. ¿Existe un hook/evento `InstructionsLoaded` (o similar) y el comando `/memory` para ver qué archivos de instrucciones están cargados? ¿Desde qué versión?
5. `--add-dir` y la variable `CLAUDE_CODE_ADDITIONAL_DIRECTORIES_CLAUDE_MD`: ¿permiten que se carguen los CLAUDE.md de otro directorio al trabajar desde un repo distinto?
6. ¿Las `@imports` dentro de CLAUDE.md pueden apuntar a rutas fuera del repo (por ejemplo `@../blog-api/CLAUDE.md`) y se cargan?
7. ¿Cómo se pueden ver las instrucciones activas durante una sesión (comando /memory, /context, etc.)?

Solo lectura/consulta: no modifiques ningún archivo. Respuesta concisa en español, estructurada por número.
```

**Qué salió:** respuesta con fuentes: los CLAUDE.md se cargan del directorio de trabajo y de sus ancestros, no de carpetas hermanas; los hooks y la configuración de proyecto tampoco se heredan entre hermanas.

## Prompt 7

**Modelo:** Claude Sonnet 5.5 (`claude-sonnet-5-5`)
**Herramienta:** Claude Code (extensión de VS Code)

```
Vamos a finalizar la Entrega 7 del Módulo 7, trabajando como Edwin Quintana (EQ).

No quiero más diagnósticos extensos, configuraciones adicionales ni pruebas innecesarias. El entorno ya funciona y la rama frontera-eq está creada en blog-api.

OBJETIVO:
Completar la práctica y preparar los dos archivos obligatorios para entregar mediante Pull Request.

1. PRÁCTICA

Utiliza esta regla:

"Toda función nueva debe incluir inmediatamente encima un comentario que describa qué devuelve cuando no encuentra resultados".

Configura la regla únicamente en blog-api mediante CLAUDE.local.md.

Realiza una modificación mínima y reversible para observar si la regla se cumple trabajando desde blog-api y qué ocurre al realizar el mismo encargo desde blog-ai.

Usa sesiones independientes si es posible. No supongas que la regla dejó de funcionar sin comprobarlo.

No instales hooks ni desarrolles mecanismos adicionales.

2. DOCUMENTACIÓN

En blog-api, rama frontera-eq:

Crea docs/frontera.md con exactamente dos frases:
- Qué hiciste para intentar que la regla se cumpliera.
- En qué momento dejó de aplicarse o, si no pudiste demostrarlo, qué observaste y cómo lo verificaste.

Completa prompts.md con los prompts originales utilizados durante la actividad, identificando herramienta y modelo. No inventes ni reconstruyas prompts que no tengas disponibles; si falta alguno, indícalo claramente.

3. LIMPIEZA

Elimina únicamente los archivos temporales creados para esta prueba.

Conserva los servicios existentes.

El Pull Request debe contener exclusivamente:
- docs/frontera.md
- prompts.md

No incluyas CLAUDE.local.md, scripts auxiliares ni código de prueba.

4. VALIDACIÓN Y ENTREGA

Comprueba:
- Rama frontera-eq.
- Que los dos documentos estén completos.
- Que las dos frases se correspondan con observaciones reales.
- Que git diff incluya únicamente los dos archivos solicitados.
- Que no se hayan modificado otros proyectos.

Después:
- Realiza commit.
- Haz push de frontera-eq al fork.
- Abre el Pull Request contra la rama de partida correspondiente del repositorio LIDR-academy-temp/blog-api-ai4devs.
- NO hagas merge.

Utiliza el nombre Edwin Quintana como autor y verifica que el correo Git configurado sea el correcto antes de crear el commit. No inventes una dirección de correo; si no está confirmado, detente antes del commit e informa.

Al finalizar, entrégame únicamente:
1. Resultado observado de la práctica.
2. Archivos entregados.
3. Commit realizado.
4. Enlace del Pull Request.
5. Confirmación de que el PR está abierto y sin merge.

Prioriza completar la entrega de manera sencilla, verificable y sin trabajo adicional fuera de lo solicitado.
```

**Qué salió:** el experimento se ejecutó con dos sesiones independientes (prompts 8 y 9) y se prepararon los dos documentos.
## Prompt 8

**Modelo:** Claude Sonnet 5.5 (`claude-sonnet-5-5`; la sesión usó además `claude-haiku-4-5` en tareas internas)
**Herramienta:** Claude Code CLI 2.1.270 (`claude -p`, sesión independiente abierta desde `blog-api`, con `CLAUDE.local.md` presente)

```
Crea un archivo nuevo llamado frontera_prueba (con la extensión del lenguaje de este proyecto) dentro de la carpeta de servicios de la aplicación. Debe contener dos funciones puras, sin dependencias del proyecto: la primera recibe una lista de posts (objetos con un campo slug) y un slug, y devuelve el post cuyo slug coincida; la segunda recibe una lista de textos y una palabra, y devuelve cuántos textos contienen esa palabra. No las conectes a ninguna ruta ni modifiques ningún otro archivo.
```

**Qué salió:** funcionó. La regla se cargó (aparece en la transcripción como instrucción de tipo Local) y las dos funciones llevaron encima `// Sin coincidencias devuelve undefined.` y `// Sin coincidencias devuelve 0.`.

## Prompt 9

**Modelo:** Claude Sonnet 5.5 (`claude-sonnet-5-5`; la sesión usó además `claude-haiku-4-5` en tareas internas)
**Herramienta:** Claude Code CLI 2.1.270 (`claude -p`, sesión independiente abierta desde `blog-ai`, sin `CLAUDE.local.md`)

```
Crea un archivo nuevo llamado frontera_prueba (con la extensión del lenguaje de este proyecto) dentro de la carpeta de servicios de la aplicación. Debe contener dos funciones puras, sin dependencias del proyecto: la primera recibe una lista de posts (objetos con un campo slug) y un slug, y devuelve el post cuyo slug coincida; la segunda recibe una lista de textos y una palabra, y devuelve cuántos textos contienen esa palabra. No las conectes a ninguna ruta ni modifiques ningún otro archivo.
```

**Qué salió:** la regla no se aplicó. Su transcripción no contiene la regla y ninguna de las dos funciones tiene un comentario encima; la primera describe el caso sin resultados solo en su docstring, dentro de la función. No hubo aviso ni error.
