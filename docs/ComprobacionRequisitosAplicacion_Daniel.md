# Comprobación de Requisitos de Seguridad de la Aplicación  

## 1. Nivel de seguridad requerido por la aplicación

La aplicación analizada es un **simulador de túnel de lavado de coches** implementado en Python puro (sin frameworks web, sin base de datos, sin API, sin autenticación, sin manejo de ficheros subidos por usuario, sin red, sin persistencia de datos sensibles).

**Características principales de la aplicación:**
- Solo dos ficheros: `lavadero.py` y `main_app.py`
- Interfaz de consola (print/input no se usa, solo prints de simulación)
- Parámetros de entrada: solo booleanos hardcodeados en ejemplos (prelavado, secado_mano, encerado)
- No hay entrada de usuario real ni datos sensibles
- No hay conexiones externas, sesiones, usuarios, logs persistentes ni almacenamiento

**Nivel ASVS recomendado: Nivel 1 (Básico)**

**Justificación:**
- No procesa datos personales, financieros ni sanitarios
- No expuesta a internet ni a usuarios no confiables
- No hay superficie de ataque significativa (sin HTTP, sin formularios, sin uploads, sin JSON/XML de terceros)
- Los únicos riesgos son errores lógicos internos (ya controlados con excepciones)
- No requiere criptografía, gestión de sesiones, control de acceso avanzado ni protección contra ataques web

Por tanto, **solo aplican los controles de Nivel 1** de los capítulos solicitados (Validación de entrada y Código malicioso). Los controles de Nivel 2 y 3 no son relevantes para esta aplicación.

## 2. Hoja de cálculo ASVS completada

- Nombre del archivo entregado: `ASVS-Checklist-Daniel.ods`
- Versión utilizada: OWASP ASVS 4.0.3 checklist
- Capítulos rellenados:  
  - **V5 – Validación de entrada y codificación de salida**  
  - **V10 – Código malicioso**

![Foto de validinputs](https://raw.githubusercontent.com/vjp-danielTM/Unidad2-TareaRA2-Daniel/refs/heads/main/docs/capturas_comprobacion_de_requisitos/1.png)


![Foto de validinputs](https://raw.githubusercontent.com/vjp-danielTM/Unidad2-TareaRA2-Daniel/refs/heads/main/docs/capturas_comprobacion_de_requisitos/2.png)


![Foto de validinputs](https://raw.githubusercontent.com/vjp-danielTM/Unidad2-TareaRA2-Daniel/refs/heads/main/docs/capturas_comprobacion_de_requisitos/3.png)


### Resumen de cumplimientos encontrados

**Capítulo V5 – Input Validation**  
| Requisito | Nivel | Estado     | Comentario breve                                                                 | Archivo referencia     |
|-----------|-------|------------|----------------------------------------------------------------------------------|------------------------|
| 5.1.1     | 1     | Non-valid  | No hay gestión de parámetros HTTP ni protección contra parameter pollution       | No aplica              |
| 5.1.2     | 1     | Valid      | No existe mass assignment; los atributos se asignan explícitamente               | lavadero.py            |
| 5.1.3     | 1     | Non-valid  | No se realiza validación positiva de entradas (aunque no hay entradas reales)    | No aplica              |
| 5.5.2     | 1     | Not Applicable | No se procesa XML en ningún momento                                             | No aplica              |
| 5.5.3     | 1     | Not Applicable | No se deserializa datos no confiables (solo booleanos internos)                 | No aplica              |

![Foto de Maliciuscode](https://raw.githubusercontent.com/vjp-danielTM/Unidad2-TareaRA2-Daniel/refs/heads/main/docs/capturas_comprobacion_de_requisitos/4.png)


**Capítulo V10 – Malicious Code**  
| Requisito | Nivel | Estado         | Comentario breve                                                                 | Archivo referencia     |
|-----------|-------|----------------|----------------------------------------------------------------------------------|------------------------|
| 10.1.1    | 3     | Not Applicable | No se usa herramienta de análisis de código malicioso (nivel 3 no aplica)        | —                      |
| 10.2.1    | 2     | Not Applicable | No hay phone-home ni recolección de datos en la aplicación                       | —                      |
| 10.2.3    | 3     | Not Applicable | No existen backdoors, cuentas hardcodeadas ni ofuscación                         | lavadero.py / main_app.py |
| 10.3.1    | 1     | Non-valid      | No existe mecanismo de auto-update firmado (no aplica porque no hay updates)     | —                      |
| 10.3.2    | 1     | Not Applicable | No se carga código dinámico desde fuentes no confiables                           | —                      |

## 5. Reflexión / valoración personal del estándar OWASP ASVS

Después de aplicar OWASP ASVS a mi simulador de lavadero de coches, aquí va mi valoración personal:

**Puntos positivos:**

- Es el estándar más completo y aceptado internacionalmente para verificar la seguridad de aplicaciones.
- Está muy bien estructurado con los tres niveles claros, lo que facilita entender qué controles son obligatorios según el riesgo.
- Cubre de forma exhaustiva desde la arquitectura y el ciclo de desarrollo seguro hasta detalles concretos como configuración HTTP, criptografía o logging.
- Obliga a pensar en seguridad desde el diseño, lo que me parece muy valioso para cualquier proyecto serio.

**Puntos negativos / limitaciones en este caso:**

- Está fuertemente orientado a aplicaciones web, por lo que gran parte de los controles no tienen sentido en una aplicación de consola como la mía.
- Para scripts locales, herramientas internas, simuladores educativos o aplicaciones batch la inmensa mayoría de los requisitos simplemente no aplican.
- El porcentaje de cobertura muy bajo puede dar una falsa sensación de que la aplicación es insegura, cuando en realidad es segura precisamente por su simplicidad y por no tener superficie de ataque expuesta.
- Rellenar la hoja completa manualmente lleva muchísimo tiempo; es mucho más práctico usar OWASP Security Knowledge Framework para generar solo los controles relevantes según el tipo de proyecto y nivel elegido.

**Conclusión personal:**

OWASP ASVS es excelente para aplicaciones web, APIs, móviles o sistemas de tamaño medio o grande con usuarios reales y exposición a internet.  
En mi caso, para un proyecto pequeño y educativo como este simulador de lavadero hecho en Python puro, sirve mucho más como herramienta de aprendizaje que como una lista de verificación estricta que haya que cumplir al cien por cien.  

Lo más valioso de esta actividad ha sido entender por qué la gran mayoría de controles no aplican a mi aplicación. Esto me ha reforzado la idea clave de que la seguridad debe ser proporcional al riesgo real de la aplicación: no todas las apps necesitan el mismo nivel de protección, y forzar controles innecesarios solo añade complejidad sin beneficio.

### Enlace al excel
[Excel Daniel](https://github.com/vjp-danielTM/ComprobacionRequisitosAplicacion_Daniel_Trujillo/blob/main/ASVS-checklist-en-DanielTrujilloMartin.ods)

#### Autor

> **_Daniel Trujillo Martin_**