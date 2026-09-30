<h1 align="center">Hola, soy Jose Carlos 👋</h1>
<h3 align="center">Desarrollador full-stack · <code>cHeKaDev</code> · aprendiendo AL/Business Central</h3>

<p align="center">
  <img src="https://img.shields.io/badge/Angular-DD0031?style=flat&logo=angular&logoColor=white" />
  <img src="https://img.shields.io/badge/NestJS-E0234E?style=flat&logo=nestjs&logoColor=white" />
  <img src="https://img.shields.io/badge/React-61DAFB?style=flat&logo=react&logoColor=black" />
  <img src="https://img.shields.io/badge/React_Native-20232A?style=flat&logo=react&logoColor=61DAFB" />
  <img src="https://img.shields.io/badge/Next.js-000000?style=flat&logo=next.js&logoColor=white" />
  <img src="https://img.shields.io/badge/Spring_Boot-6DB33F?style=flat&logo=springboot&logoColor=white" />
  <img src="https://img.shields.io/badge/Node.js-339933?style=flat&logo=node.js&logoColor=white" />
  <img src="https://img.shields.io/badge/MongoDB-47A248?style=flat&logo=mongodb&logoColor=white" />
  <img src="https://img.shields.io/badge/PostgreSQL-4169E1?style=flat&logo=postgresql&logoColor=white" />
  <img src="https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white" />
  <img src="https://img.shields.io/badge/Docker-2496ED?style=flat&logo=docker&logoColor=white" />
  <img src="https://img.shields.io/badge/OpenAI%20%2F%20DeepSeek-412991?style=flat&logo=openai&logoColor=white" />
  <img src="https://img.shields.io/badge/AL%20%2F%20Business%20Central-002050?style=flat&logo=microsoft&logoColor=white" />
</p>

Programo desde hace unos meses por mi cuenta una vez terminado el Grado Superior de DAM, con proyectos reales de principio a fin: backend, frontend web, apps móviles e integraciones con IA. Ahora mismo estoy formándome en **AL (Business Central)**, así que si buscas a alguien que aprende rápido y con dedicación, aquí tienes prueba de ello.

Tambien tengo una especialidad de Desarrollo con IA en Big School, con el que he desarrollado aplicaciones aplicando todos los conocimientos adquiridos y los nuevos que he ido aprendiendo por el camino, aunque me falta mucho camino para acabar desarrollando como un senior.

La mayoría de mis repositorios son **privados** (código de clientes/proyectos propios), pero aquí abajo tienes el detalle real de cada uno. Si quieres ver código, escríbeme y te doy acceso.

---

### 🐾 VetClinic — TFG
Mi primer proyecto y al que mas cariño le tengo ya que esta desarrollado enteramente por mi con muchisimas horas dedicadas(quebraderos de cabeza y mucha ansiedad hasta conseguir un resultado optimo) y para un sector que me toca muy de cerca.

Suite de tres repos: `apiclinica` (NestJS + MongoDB, JWT + roles Admin/Trabajador/Cliente, módulo de IA con vector store de OpenAI), `clinica_crud` (panel Angular) y `appMovil` (app Ionic/Angular para clientes, con chat IA). Trabajo Fin de Grado — proyecto académico, sin el mismo proceso de specs que los de arriba.

## 🤖 Cómo trabajo con IA

Los proyectos marcados con 🤖 están construidos con IA como colaborador de desarrollo, no como autocompletado. El proceso es siempre el mismo, y es verificable en el propio repo:

- **Spec-driven development.** Cada funcionalidad se especifica antes de tocar código: objetivo, quién la usa, comportamiento esperado en formato Given/When/Then, y criterios de aceptación numerados (`CA-1`, `CA-2`...). La spec es la fuente de verdad — si algo no encaja al implementar, se actualiza la spec primero. Solo en el ERP interno de ChekNologies esto son **más de 3.500 líneas de specs** repartidas en 5 documentos (pedidos/stock, presupuestos, app móvil, RRHH, contabilidad).
- **Desarrollo por fases cerradas.** Nunca se empieza la fase N+1 sin que la N esté implementada, verificada con tests y comiteada por separado. El proyecto D&D con IA Master tiene 10 documentos de diseño (01–10) siguiendo este esquema.
- **TDD estricto**, no solo tests al final: dominio y casos de uso se desarrollan en rojo-verde-refactor, con dobles/fakes en memoria para no depender de infraestructura real en los tests. Ejemplos con número real de tests: TPV Tienda (234 unitarios API + 68 web + 41 de integración contra Mongo real), ERP interno (48 JUnit5 + 7 Mockito), D&D (`FakeDiceRoller` y otros dobles en domain/application).
- **Arquitectura hexagonal / Clean Architecture como norma, no como excusa**: `domain/` sin una sola dependencia de framework, `application/` con casos de uso y los puertos que ellos mismos definen, `infrastructure/` con los adaptadores reales. Cambiar de proveedor (LLM, base de datos, sandbox de ejecución) es escribir un adaptador nuevo, no tocar el dominio.
- **Auditorías de seguridad explícitas y testeadas**, no solo "debería funcionar": por ejemplo, en el TPV hay un test que demuestra que la autenticación de página nunca sustituye a la autenticación de la API de datos, llamando a la API sin la cabecera esperada.
- **Prompts de arranque estructurados y documentados** (contexto y rol, tarea, especificaciones, criterios de calidad, formato de respuesta esperado) en vez de pedir "hazme una web de..." — quedan en el propio repo como parte del proceso, no se tiran.

Ejemplo de hasta dónde llega esto: **CodeConsensus** (detalle completo más abajo) — un proyecto que automatiza literalmente este mismo proceso de revisión: varias IAs locales debaten un problema, una propone código, otras lo critican y votan, y nada se declara "consensuado" si no pasa sus tests y su linter en un sandbox real.

---

## 🧩 Ecosistema ChekNologies — mi estudio de software

Tres repos independientes que forman el mismo producto: captación (web + agente de voz IA), gestión interna (ERP) y trabajo en calle (app móvil).

### 🌐 Web ChekNologies 🤖
Landing page en Next.js (App Router) + TypeScript, sin librerías de UI — CSS puro con variables de marca. Integra un **agente de voz/chat con IA (Retell)**: dos rutas de API propias hacen de proxy para que la API key de Retell nunca llegue al navegador; si faltan las variables de entorno, el propio widget lo avisa en el chat en vez de fallar en silencio. Los leads que capta el agente de voz llegan directamente al ERP interno vía webhook.

### 🏢 CRM/ERP interno 🤖 (`demo-crm-erp`)
Panel interno para gestionar los leads del agente de voz, clientes, proveedores, productos con inventario, pedidos y facturación interna.

- **Backend:** Spring Boot 3 (Java 21) + Maven — dominio con TDD (`Familia`, `Cliente`, `Proveedor`, `Producto` con reglas de stock, `Lead`, `Pedido`, `Factura`), casos de uso `ConfirmarPedidoVenta`/`ConfirmarPedidoCompra` con puertos + Mockito, migraciones Flyway (8 ficheros SQL) y repositorios JDBC reales contra Postgres
- **Frontend:** Next.js + TypeScript, cliente puro de la API sin lógica de negocio propia
- Empezó entero en Next.js/Node y se **rehízo el backend en Spring Boot** a propósito, para acercarlo al stack real de un puesto de backend Java — decisión documentada, no casualidad
- Monorepo con Docker Compose (`db` + `api` + `web`), cada carpeta con su propio Dockerfile
- Reglas de confirmación de pedido con lógica real: una venta sin stock suficiente en **cualquier** línea no confirma nada ("todo o nada"); una compra nunca falla por stock

### 📱 CRM Móvil 🤖
App Android (Expo/React Native) para que el equipo comercial consulte leads, clientes y agenda desde la calle — nada de productos, pedidos ni facturación, ni para el admin (alcance recortado a propósito y documentado en la spec del ERP).

- Autenticación por sesión propia (no JWT compartido): token individual por comercial, revocable desde base de datos sin afectar a los demás, cifrado en el dispositivo (`expo-secure-store`)
- Permisos por rol: comercial/admin entran, contabilidad/logística reciben 403 aunque la contraseña sea correcta
- Decisión documentada y deliberada de **no usar librería de navegación** (tres pestañas con `useState`) para no arriesgar la compilación con el SDK de Expo

---

## 🎓 TFM, TFG y proyectos personales

### 🧠 CodeConsensus 🔒 🤖
Herramienta para que varias IAs locales (Ollama, 100% en la máquina, nada sale a la nube) debatan un mismo problema hasta llegar a código consensuado: un **Autor** propone, varios **Revisores** lo critican por severidad y votan, un **Juez** desempata si hace falta, y un sandbox Docker ejecuta tests y linter — el consenso entre IAs nunca vale más que ese resultado objetivo.

- NestJS + TypeScript, **arquitectura hexagonal** real: `domain/` (`Debate`, `Ronda`, `Problema`, `RegladeConsenso`...) sin una sola dependencia de framework, `application/` con los casos de uso y sus puertos (`LlmProvider`, `CodeSandbox`, `DebateRepository`), `infrastructure/` con los adaptadores (Ollama, MongoDB)
- **TDD estricto de verdad, no de boquilla**: 429 tests (`it()`) repartidos en 20 ficheros — solo el dominio del propio `Debate` tiene 55 tests en 600 líneas — con dobles en memoria (`LlmProvider` falso, repositorio en memoria) para no depender de Ollama ni Mongo reales en los tests
- Salida estructurada obligatoria (JSON Schema) tanto para el Autor como para los Revisores, validada y con reintento automático si el LLM devuelve algo inválido
- Máquina de estados de dominio explícita para el debate, con reanudación tras un reinicio del backend (retoma desde la última ronda completa, con tope de reintentos para no entrar en bucle)
- Spec propia de 5 fases con 34 criterios de aceptación (`CA-1`...`CA-34`); ahora mismo la **Fase 1 (MVP del debate)** está implementada y en desarrollo

### 🎲 D&D con IA Master 🤖 — *Trabajo Fin de Máster*
Sistema de rol D&D 5e donde una IA (DeepSeek) hace de Dungeon Master, con tiradas de dados deterministas resueltas siempre en servidor (la IA narra, nunca inventa resultados).

- **`API_REST`** — NestJS 11 + MongoDB, Clean Architecture, TDD estricto (dobles/fakes), servidor **MCP propio con 26 herramientas**, síntesis de voz (Qwen3-TTS-Flash)
- **`dm-engine`** — motor de orquestación en Node/Express que conecta con DeepSeek (compatible con otros LLMs)
- **`ui-web`** — interfaz web de solo lectura en React 18 + Vite
- **`mobile-app`** — app en React Native/Expo, la superficie principal de juego
- 10 documentos de diseño (01–10) cubriendo spec, modelo de datos, arquitectura, MCP, motor de IA, CI/CD y autenticación

Desplegado y funcionando en producción: **[web](https://ui-web-three.vercel.app/login)** · **[API](https://api-dnd5e-dm-ia.onrender.com)** · APK de Android disponible bajo petición.

### 📄 RAG de Facturas con IA 🔒 🤖
Banco de pruebas del módulo de IA documental de ChekNologies: sube facturas, las indexa y responde preguntas sobre ellas en lenguaje natural, con un mapa visual de los vectores.

- **Backend:** Python + FastAPI, **arquitectura hexagonal** (`domain/` sin dependencias, `application/` con puertos y casos de uso, `infrastructure/` con los adaptadores reales) · `main.py` como único composition root
- **Lectura inteligente de PDFs:** si el PDF tiene texto real se extrae con `pypdf` sin coste; si es un escaneado o una imagen, cada página pasa por **GPT-4o Vision** (hasta 20 páginas por documento, para acotar el gasto)
- **Búsqueda:** embeddings (`text-embedding-3-small`) sobre **ChromaDB**; al modelo le llega la factura completa relevante, no fragmentos sueltos, para no perder datos como el importe total — y hay una vista que muestra exactamente qué texto quedó indexado
- **Mapa vectorial** de las facturas con UMAP, para inspeccionar visualmente cómo se agrupan
- **Seguridad real, no de fachada:** cookie de sesión firmada (`HttpOnly`, `Secure`, `SameSite=Strict`) que caduca a los 5 min de inactividad, verificada en **cada ruta de datos** de la API (no solo en la página de login) más una clave interna que añade nginx en el proxy web→api; límite de 10 intentos de login por minuto
- **75 tests** (pytest) con un cliente de OpenAI falso, sin red ni coste real en los tests
- Desplegado en el homelab propio vía Docker Compose + Coolify + Cloudflare Tunnel, integrado con el ERP de ChekNologies (comparte clave de OpenAI)

### 🛒 TPV Tienda 🔒 🤖
Punto de venta con control de stock para un único PC con Windows, con instalador propio.

- NestJS (API) + web (BFF) sobre **Clean Architecture** (`domain` sin dependencias de framework, `application`, `infrastructure`)
- MongoDB con transacciones reales (replica set), migraciones versionadas
- Emisión de tickets/facturas en PDF, lectura por código de barras
- **Instalador nativo de Windows** con Inno Setup + servicio WinSW
- Suite de tests seria: 234 unitarios (API) + 68 (web) + 41 de integración contra Mongo real
- Preparado de cara a la normativa **Veri\*Factu** (obligatoria en España en 2027)


---

## 📊 Actividad

<p align="center">
  <img src="https://github-readme-stats.vercel.app/api?username=checacs&show_icons=true&count_private=true&theme=default" />
</p>

> Para que esta tarjeta refleje también el trabajo en repos privados, hay que activar **"Include private contributions"** en `Settings → Profile` de GitHub.

---

## 📫 Contacto

- ✉️ checacs@gmail.com
- 💻 [github.com/checacs](https://github.com/checacs)
