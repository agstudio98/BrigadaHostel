# Panel de Administración — BrigadaHostel

> Interfaz interna de gestión operativa para el sistema de administración de BrigadaHostel. Diseñada con foco en usabilidad, rendimiento y mantenibilidad a largo plazo.

---

## Índice

1. [Descripción General](#descripción-general)
2. [Acceso y Autenticación](#acceso-y-autenticación)
3. [Módulos del Panel](#módulos-del-panel)
   - [Dashboard — Resumen General](#dashboard--resumen-general)
   - [Reservas — Flujo de Registro](#reservas--flujo-de-registro)
   - [Recepción — Operatividad Diaria](#recepción--operatividad-diaria)
   - [Huéspedes — Análisis de Huéspedes](#huéspedes--análisis-de-huéspedes)
   - [Operaciones — Operaciones y Eficiencia](#operaciones--operaciones-y-eficiencia)
   - [Métricas — Métricas Financieras y Operativas](#métricas--métricas-financieras-y-operativas)
   - [Configuración — Ajustes del Sistema](#configuración--ajustes-del-sistema)
4. [Navegación y Estructura Compartida](#navegación-y-estructura-compartida)
5. [Aspectos Técnicos](#aspectos-técnicos)
6. [Sistema de Branching y Organización](#sistema-de-branching-y-organización)

---

## Descripción General

BrigadaHostel Admin es un panel de administración interno compuesto por páginas HTML estáticas con estilos centralizados en un único archivo CSS. No depende de frameworks JavaScript ni de un backend activo para funcionar: toda la lógica de navegación, menús y layout está resuelta a nivel de CSS puro.

El panel está orientado al personal administrativo del hostel y cubre múltiples áreas operativas:

- análisis de rendimiento,
- gestión de reservas,
- control de recepción,
- análisis de huéspedes,
- monitoreo operativo,
- métricas financieras,
- configuración del sistema.

El objetivo principal es centralizar la administración interna del hostel en una interfaz moderna, responsive y fácilmente mantenible.

---

## Acceso y Autenticación

El ingreso al panel se realiza a través de dos páginas dedicadas que comparten la misma estética visual del sistema.

### Login (`loginDashboard.html`)
Formulario de acceso con dos campos: email y contraseña. Al enviar el formulario, el usuario es redirigido directamente a `dashboard.html`. Incluye un enlace para crear una cuenta nueva.

### Registro (`signupDashboard.html`)
Formulario de alta de nuevo usuario administrativo con los campos: nombre, apellido, email y contraseña (mínimo 8 caracteres, validado con `minlength`). Al completarse, redirige al login.

> **Nota:** El título del `<head>` contiene un typo menor (`Singup`) que puede corregirse por `Signup`.

Ambas páginas muestran el logo del hostel y la tarjeta de autenticación centrada con estilo visual compartido con el resto del sistema.

---

## Módulos del Panel

### Dashboard — Gestión según Rol

El Dashboard ha sido rediseñado para ofrecer una experiencia diferenciada según el perfil del usuario, eliminando métricas genéricas y enfocándose en la operatividad real de un hostel.

-   **Vista Administrador**: Enfocada en el rendimiento del negocio (Ocupación mensual, Ingresos del día, Total de reservas activas).
-   **Vista Staff (Recepcionista)**: Enfocada en la operativa diaria (Check-ins pendientes, Habitaciones por limpiar, Disponibilidad inmediata).
-   **Listado de Actividad**: Una sección común para monitorear los movimientos recientes de huéspedes.

---

### Reservas — Flujo de Registro

Siguiendo el modelado de Casos de Uso, el proceso de registro se ha simplificado en 3 pasos clave dentro del sistema de recepción:

1.  **Verificar Disponibilidad**: El recepcionista ingresa datos del huésped y fechas para consultar el inventario libre.
2.  **Habitación y Servicios**: Selección de la habitación disponible y agregado de servicios extra (Desayuno, Cochera, etc.).
3.  **Confirmar y Registrar**: Resumen de costos totales con impuestos y confirmación final para persistencia en el sistema.

Este flujo unifica la "Reserva de Habitación" con el "Registrar Reserva", eliminando redundancias conceptuales.

---

### Recepción — Operatividad Diaria

Módulo orientado al trabajo operativo del mostrador y gestión diaria de huéspedes. Combina métricas operativas en tiempo real con herramientas administrativas.

**Métricas rápidas:**

| Métrica | Valor de ejemplo |
|---|---|
| Productividad del Staff | 142 gestiones (+12 hoy) |
| No-Show Rate | 2.1% (▼ mejora) |
| Tiempo Promedio de Check-in | 4.5 min (▼ mejorado) |
| Ingresos en Mostrador | $1,240 (▲ 15% venta directa) |

**Secciones de análisis:**

- **Ocupación Real Diaria** — Círculo de progreso CSS: 18 de 24 habitaciones ocupadas (85%).
- **Estado de Inventario** — Distribución visual: Ocupadas (18), Limpias (4), Sucias (2), En Mantenimiento (0).
- **Modificaciones Manuales** — Gráfico de barras por día para monitorear ajustes en recepción.
- **Origen de Cancelaciones** — Admin/Recepción (45%) vs autogestión del usuario (55%).
- **Previsión de Check-outs** — Visualización de salidas programadas para próximos días.
- **Discrepancia de Montos** — Alerta en rojo con diferencias entre montos calculados y cobrados (+$245.00 de ejemplo).

**Tabla de gestión:** Lista de huéspedes activos con habitación, estado y acciones rápidas por fila (Actualizar, Check-out, Reportar).

---

### Huéspedes — Análisis de Huéspedes

> Responsable: [@Alejo Camolotto](https://github.com/Camolotto)

Permite comprender el perfil y comportamiento de los visitantes mediante datos demográficos y patrones de estadía.

Incluye información sobre:
- Nacionalidades principales
- Rangos de edad
- Motivos del viaje
- Nivel de fidelización

Estas métricas ayudan a identificar el público objetivo, adaptar servicios, optimizar estrategias de marketing y aumentar la retención de clientes recurrentes.

**Funcionalidades principales:**
- Distribución por nacionalidades
- Segmentación por edades
- Motivos frecuentes de viaje
- Huéspedes recurrentes
- Estadísticas visuales
- Análisis demográfico general

---

### Operaciones — Operaciones y Eficiencia

> Responsable: [@Giuliano Batistella](https://github.com/gbatistela)

Muestra el estado operativo interno del hostel y permite monitorear el rendimiento diario del personal y los recursos. Incluye métricas de limpieza, mantenimiento, inventario, consumo energético y atención al huésped.

**Objetivos:** optimizar procesos internos, mejorar eficiencia operativa, reducir costos y mantener calidad de servicio.

**Funcionalidades principales:**
- Seguimiento de limpieza
- Estado de inventario
- Consumo de energía
- Tiempo de respuesta al huésped
- Rendimiento operativo diario
- Gestión de recursos internos

---

### Métricas — Métricas Financieras y Operativas

> Responsable: [@Mauricio Ferreyra](https://github.com/EmiTeck)

Panel financiero y operativo del hostel con indicadores clave de rendimiento.

**Indicadores principales:**

- **RevPAR** — Ingreso por habitación disponible con evolución mensual.
- **ADR (Average Daily Rate)** — Tarifa diaria promedio de reservas.
- **Ocupación por tipo de habitación** — Análisis de ocupación segmentado.
- **ROI de campañas de marketing** — Retorno de inversión de campañas promocionales.

**Objetivos del módulo:** evaluar rentabilidad, medir crecimiento, analizar eficiencia operativa y visualizar desempeño comercial.

---

### Configuración — Ajustes del Sistema

Módulo de personalización de la cuenta y el entorno del administrador.

**Métricas de estado:**

| Indicador | Valor |
|---|---|
| Estado de Cuenta | Verificada — Seguridad Alta |
| Rol de Usuario | Super Admin — Acceso Total |
| Último Cambio de Contraseña | Hace 12 días (próximo en 78 días) |
| Versión del Sistema | v2.4.8-stable |

**Secciones:**

- **Perfil de Administrador** — Foto de perfil (JPG/PNG, máx. 800K), nombre completo y email de contacto.
- **Preferencias Visuales** — Idioma (Español, English, Português), tema Claro/Oscuro y Modo Compacto.
- **Alertas y Notificaciones** — Nuevas Reservas (email), Reporte de Turno y Alertas SMS.
- **Seguridad y Acceso** — Estado de 2FA, cambio de contraseña y registro de sesiones activas.

---

## Navegación y Estructura Compartida

Todas las páginas del panel comparten los mismos componentes reutilizables:

- **Sidebar** — Logo, navegación principal, Cerrar Sesión y Volver al sitio web.
- **Header** — Título actual, subtítulo, usuario activo y avatar.
- **Botón hamburguesa** — Visible únicamente en dispositivos móviles. Controla la apertura y cierre del sidebar.

El enlace activo en la barra lateral utiliza la clase `active`.

---

## Aspectos Técnicos

### Navegación Mobile sin JavaScript
El menú lateral mobile se controla con un `<input type="checkbox" id="menu-cb" hidden>` y un `<label for="menu-cb">` como disparador visual. Al activarse, aparece un overlay y se despliega el sidebar sin requerir JavaScript, garantizando compatibilidad total y carga instantánea.

### Diseño Adaptativo
Las tablas se transforman automáticamente en tarjetas apiladas usando el atributo `data-label` en cada celda `<td>`, manteniendo compatibilidad responsive en pantallas pequeñas.

### Centralización de Estilos
Todos los módulos utilizan un único archivo `dashboard.css`. Esto permite mantenimiento simplificado, consistencia visual y reutilización de componentes en todo el panel.

---

## Sistema de Branching y Organización

El proyecto utiliza una metodología basada en ramas para facilitar el trabajo colaborativo.

### Estructura de ramas

- `main` → versión estable final
- `develop` → integración general
- `feature/*` → desarrollo individual


### Flujo de trabajo

1. Crear rama desde `develop`
2. Desarrollar el módulo correspondiente
3. Realizar commits descriptivos
4. Subir cambios al repositorio
5. Realizar merge hacia `develop`

### Roles

| Área | Responsable |
|---|---|
| Inicio / Home | [Oscar Quevedo](https://github.com/Oscar-Quevedo) |
| Sobre Nosotros | [Jorge Quevedo](https://github.com/JQuevedoJorge) |
| Dashboard | [Agusin Gallardo](https://github.com/agstudio98) |
| Métricas + Caso de Uso | [Mauricio Ferreyra](https://github.com/EmiTeck) |
| Operaciones + Diagramas | [Giuliano Batistella](https://github.com/gbatistela) |
| Huéspedes + README + Branching | [Alejo Camolotto](https://github.com/Camolotto) |

> En caso de dificultades utilizando Git por terminal, también pueden realizarse modificaciones directamente desde GitHub mediante edición web y commits manuales.

---

## Herramientas y Asistencia de IA

Este proyecto ha contado con la asistencia de **Gemini CLI** para tareas de refactorización, optimización de estilos y organización de repositorio. 

**Nota de Responsabilidad:** 
Como equipo, asumimos la responsabilidad total sobre el código incluido. Comprendemos que todo código generado por IA o basado en plantillas debe ser revisado, comprendido y validado antes de su integración final para asegurar su correcto funcionamiento y mantenimiento.

---

## About

Proyecto de Evidencia 1 — Sistema de administración hotelera.
Prototipo básico realizado como sitio estático responsive orientado a gestión interna.

## Contributors

| | |
|---|---|
| [@agstudio98](https://github.com/agstudio98) | Agustín Gallardo |
| [@Oscar-Quevedo](https://github.com/Oscar-Quevedo) | Oscar Quevedo |
| [@JQuevedoJorge](https://github.com/JQuevedoJorge) | Jorge Quevedo |
| [@Camolotto](https://github.com/Camolotto) | Alejo Camolotto |
| [@gbatistela](https://github.com/gbatistela) | Giuliano Batistella |
| [@EmiTeck](https://github.com/EmiTeck) | Mauricio Ferreyra |

## Languages

- HTML
- CSS
