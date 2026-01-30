# Tarea Unidad 2 - DANIEL TRUJILLO

Documentación de la Unidad 2. Esta entrega recoge el trabajo realizado sobre análisis de vulnerabilidades, explotación práctica, aplicación de estándares de seguridad y reflexión sobre riesgos en aplicaciones.

---

**Contenido (en el orden solicitado):**

### 1. [Trazado de Vulnerabilidad – CVE-2024-0204](TrazadoVulnerabilidadGoAnywhere.md)

Análisis detallado de la vulnerabilidad **CVE-2024-0204** (asociada a GoAnywhere MFT).

Incluye:

- Descripción oficial, puntuación CVSS y vector de ataque (NVD)
- CWE relacionado: CWE-425 (Direct Request / Forced Browsing)
- CAPEC asociados: Forced Browsing, Directory Indexing, Detect Unpublicized Pages/Services, etc.
- Explicación de la debilidad y patrones de ataque
- Medidas de mitigación recomendadas
- Descarga del registro CVE en formato JSON

### 2. [Máquina Vulnerable bWAPP – SQL Injection](MaquinaVulnerable.md)

Documentación de la explotación de la vulnerabilidad **SQL Injection (GET/SELECT)** en bWAPP, analizando los niveles low, medium y high.

Se detalla:

- Identificación del parámetro vulnerable (`movie`) en la URL
- Explotación con UNION SELECT para extraer el nombre de la base de datos
- Comportamiento diferencial en cada nivel de seguridad
- Análisis del código fuente (`sqli_2.php`)
- Estudio de las funciones de protección: `no_check` vs `sqli_check_2` (`mysql_real_escape_string`)

### 3. [Comprobación de Requisitos de Seguridad](ComprobacionRequisitosAplicacion_Daniel.md)

Aplicación del estándar **OWASP ASVS 4.0.3** al simulador de túnel de lavado de coches (Python – aplicación de consola sin red ni datos sensibles).

Contenido principal:

- Justificación del nivel recomendado: **Nivel 1 (básico)**
- Revisión detallada de los capítulos V5 (Validación de entrada y codificación de salida) y V10 (Código malicioso)
- Tablas resumen de requisitos aplicables, no aplicables y cumplimientos
- Reflexión personal sobre las limitaciones del estándar ASVS en aplicaciones minimalistas/no-web
- Enlace al archivo `.ods` completado

### 4. [Reflexión sobre los riesgos de las aplicaciones](Conclusiones_Daniel.md)

Análisis comparativo de los riesgos de seguridad según el tipo y características de la aplicación.

Se compara la aplicación del proyecto (simulador de lavadero – Python consola, sin exposición ni datos sensibles) con:

- Aplicaciones bancarias
- Aplicaciones de salud / historial clínico
- Aplicaciones de redes sociales

Conclusión clave:  
**El nivel de riesgo depende principalmente del valor de los datos manejados, la exposición a internet/usuarios no confiables y la complejidad/integraciones externas de la aplicación.**

---

- **Repositorio de GitHub (Unidad 2)**: [Repositorio Unidad2-TareaRA2-Daniel](https://github.com/vjp-danielTM/Unidad2-TareaRA2-Daniel)

---

#### Autor

> **_Daniel Trujillo Martin_** 