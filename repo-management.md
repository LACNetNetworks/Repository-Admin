# 📘 Procedimiento de Gestión de Repositorios en GitHub

## 1. Objetivo
Establecer una política clara, segura y auditable para la creación, administración, migración y control de acceso a repositorios en GitHub, para proyectos <b>LACChain y LACNet</b>.

## 2. Alcance
Este procedimiento aplica a todos los miembros de la organización que requieran crear, migrar o administrar repositorios en GitHub.

## 3. Requisitos Generales

- Todos los miembros de la organización deben tener activado **2FA (autenticación en dos factores)**.
- Todo repositorio debe estar asociado a la **Organización oficial en GitHub**.
- Se prioriza el uso de **equipos** sobre usuarios individuales para asignación de permisos.
- El uso de ramas protegidas y flujos de trabajo con PR es obligatorio en proyectos productivos.

---

## 4. Solicitud de Creación de Repositorio

Todas las solicutudes especificadas en este documento deberan ser creadas mediante el sistema de tickets de soporte de LACNet:
https://lac-net.atlassian.net/servicedesk/customer/portal/3 (New request)


### 4.1 Formato de Solicitud

El usuario debe enviar una solicitud con los siguientes datos:

- Nombre del repositorio (sugerido)
- Propósito del repositorio
- Visibilidad: `public`, `private` o `internal`
- Nivel de acceso requerido por equipo o usuario
- Equipo responsable (owner)
- Tags propuestos (`infraestructura`, `backend`, etc.)


### 4.2 Aprobación

El equipo técnico revisará:

- Coherencia del nombre y si ya existe un repositorio similar
- Adecuación del nivel de acceso solicitado
- Cumplimiento de estándares de seguridad y organización

> ** El Feedback se respondera en Ticket cargado **

### 4.3 Creación

Una vez aprobado, el equipo DevOps o administrador creará el repositorio incluyendo:

- `README.md`, `.gitignore`, `LICENSE`
- Plantillas de Issues y PRs (si aplica)
- Protección de ramas
- Asignación de equipos y permisos

---

## 5. Solicitud de Migración de Repositorio

### 5.1 Casos Válidos

- Migración de repositorios personales o de otras organizaciones a la organización actual.
- Unificación de repositorios dispersos en un repositorio consolidado.
- Migración entre plataformas (GitLab, Bitbucket, etc.) hacia GitHub.

### 5.2 Formato de Solicitud

- URL del repositorio original
- Responsable técnico de la migración
- Justificación y objetivo
- Repositorio de destino (nuevo o existente)

### 5.3 Procedimiento

- Validar que se tenga acceso de tipo `admin` o `maintainer` al repositorio fuente.
- Exportar todo el historial (`git clone --mirror`) si es posible.
- Crear el repositorio destino bajo la organización.
- Importar con `git push --mirror`.

> **Nota**: Si no se tiene acceso de tipo `admin/maintainer` al repositorio original, se deberá gestionar previamente el acceso o solicitar colaboración del propietario original.

---

## 6. Gestión de Permisos

### 6.1 Permisos Estándar

| Rol GitHub     | Descripción                                        |
|----------------|----------------------------------------------------|
| `Read`         | Lectura de código e Issues                         |
| `Triage`       | Gestión de Issues y Pull Requests                  |
| `Write`        | Push directo, creación de ramas                    |
| `Maintain`     | Gestión de configuración del repo, sin eliminarlo |
| `Admin`        | Control total, incluidos settings y equipos        |

### 6.2 Procedimiento

1. Enviar solicitud con:
   - Repositorio
   - Usuario o equipo
   - Permiso requerido
   - Justificación

2. El equipo DevOps evaluará:
   - Necesidad real del permiso solicitado
   - Posible impacto en la seguridad o estabilidad

3. Toda modificación será registrada en el sistema de tickets o changelog.

### 6.3 Consideración sobre permisos limitados

> ⚠ **Aclaración importante:** No todos los administradores de proyectos tienen permisos de tipo `maintainer` o `admin` en los repositorios. En estos casos, cualquier solicitud de permisos o configuraciones deberá ser derivada a un administrador organizacional. La gestión descentralizada debe respetar los límites de acceso para preservar la seguridad y gobernanza de los repositorios.

---

## 7. Requisitos de Seguridad

- ✅ **2FA obligatorio** para todos los miembros de la organización
- 🔒 Protección de rama `main` (o rama principal)
  - Revisión de al menos 1 miembro del equipo
  - CI/CD exitoso obligatorio antes del merge
- 🧾 Revisión semanal de tokens y accesos personales
- 🔍 Auditoría mensual de permisos elevados (`admin`, `maintain`)

---

## 8. Auditoría y Mantenimiento

### 8.1 Revisión Trimestral

- Identificación de repos inactivos (sin commits en 6 meses)
- Limpieza de permisos innecesarios
- Revisión de documentación mínima

### 8.2 Archivado o Eliminación

- Repositorios inactivos pueden ser:
  - Archivados (solo lectura)
  - Eliminados tras aprobación del responsable técnico

---

## 9. Buenas Prácticas

- Usar `README.md`, `LICENSE` y `CONTRIBUTING.md` en todos los repos
- Etiquetar repos con tópicos relevantes
- Documentar dependencias externas y configuración de entorno
- Usar `CODEOWNERS` para automatizar revisiones y asignaciones

---

## 10. Responsables

| Área           | Función                                         |
|----------------|-------------------------------------------------|
| **DevOps**     | Implementación técnica, seguridad y permisos    |
| **Proyecto**   | Definición de necesidades y validaciones        |
| **Seguridad**  | Auditoría periódica de accesos y 2FA            |

---

> Para dudas o solicitudes, contactarse con el equipo DevOps a través del sistema de tickets oficial o canal designado.
