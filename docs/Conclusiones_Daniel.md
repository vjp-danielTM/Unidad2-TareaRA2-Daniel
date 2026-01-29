# Apartado 4 - Reflexión sobre los riesgos de las aplicaciones

## Introducción
En esta reflexión personal analizo los riesgos de seguridad asociados a la aplicación que hemos utilizado en el apartado anterior: un simulador de túnel de lavado de coches implementado en Python con los archivos `lavadero.py` y `main_app.py`. Se trata de una aplicación simple de consola, sin interfaz web, sin manejo de datos reales de usuarios y sin conexiones externas. A partir de ahí comparo estos riesgos con los de otros tipos de aplicaciones más complejas, como las bancarias, de salud o de redes sociales, para destacar cómo los riesgos dependen directamente de las características de cada aplicación.

Esta reflexión surge de lo aprendido al aplicar OWASP ASVS en la actividad anterior, donde vi que la mayoría de controles de seguridad no aplicaban a mi app precisamente por su simplicidad.

## Riesgos de la aplicación simulador de lavadero de coches
Mi aplicación es un script Python puro que simula fases de lavado con parámetros booleanos hardcodeados (prelavado, secado a mano, encerado). No interactúa con usuarios reales, no almacena datos, no usa redes ni depende de bibliotecas externas vulnerables. Por tanto sus riesgos son mínimos y principalmente internos o teóricos:

- **Riesgos lógicos internos**  
  Podría haber errores en la lógica de negocio, como un bucle infinito en las fases (aunque lo controlo con contadores) o excepciones no manejadas que hagan fallar el programa. Esto no es un riesgo de seguridad real, sino de estabilidad. En ASVS se relaciona con controles de "Business Logic" (V11), pero en mi caso no aplica porque no hay transacciones reales.

- **Ausencia de riesgos externos**  
  No hay inyecciones SQL, XSS ni CSRF porque no hay entradas de usuario ni web. No hay fugas de datos porque no se manejan datos sensibles. No hay riesgos de autenticación ni sesiones porque no hay usuarios. En el análisis ASVS, la mayoría de capítulos (Autenticación, Sesión, Criptografía…) quedaron como "Not Applicable" por esta razón.

- **Riesgos potenciales si se expande**  
  Si la convirtiera en una aplicación web (por ejemplo con Flask), aparecerían riesgos como validación de entradas insuficiente (V5 en ASVS), que podrían llevar a inyecciones o denegación de servicio. Pero en su estado actual el riesgo es casi nulo: es segura por su diseño minimalista.

Los riesgos son bajos porque la app es offline, local y sin datos sensibles. No expone superficie de ataque, por lo que no necesita altos niveles de ASVS (quedé en Nivel 1 con baja cobertura, pero sin vulnerabilidades reales).

## Comparación con otros tipos de aplicaciones
Los riesgos no son universales; dependen de las características de cada aplicación. A continuación comparo con tres tipos muy diferentes:

### Aplicaciones bancarias
- **Características clave**  
  Manejan datos financieros (cuentas, transacciones, saldos), requieren autenticación fuerte (MFA), conexiones seguras (TLS), integración con APIs externas y cumplimiento normativo (PSD2, PCI-DSS).

- **Riesgos principales**  
  Muy altos. Incluyen robo de credenciales (phishing, credential stuffing), fraude en transacciones (man-in-the-middle), inyecciones en APIs (SQLi), ransomware que bloquee accesos o lavado de dinero mediante exploits en lógica de negocio. Un breach puede causar pérdidas económicas directas y daños reputacionales graves.

### Aplicaciones de salud (historial médico, telemedicina)
- **Características clave**  
  Procesan datos sanitarios sensibles (diagnósticos, historial clínico, recetas), cumplen regulaciones estrictas (GDPR, HIPAA), suelen tener integración con dispositivos médicos y accesos por múltiples roles (pacientes, médicos, administrativos).

- **Riesgos principales**  
  Extremadamente altos. Exposición de datos personales sensibles puede llevar a extorsión, discriminación o daños a la salud si se altera información (por ejemplo cambiando una dosis). También hay riesgos de denegación de servicio que impidan acceso urgente a historiales en emergencias.

### Aplicaciones de redes sociales (RRSS)
- **Características clave**  
  Gestionan perfiles de millones de usuarios, contenido generado por usuarios, interacciones en tiempo real, algoritmos de recomendación, anuncios y moderación de contenido.

- **Riesgos principales**  
  Altos y variados. Incluyen abuso de cuentas (phishing, bots), difusión masiva de desinformación, acoso y doxxing, fugas masivas de datos (scraping de perfiles), manipulación algorítmica y riesgos de privacidad (geolocalización, metadatos de fotos). Un incidente puede afectar a millones de usuarios rápidamente.

## Conclusión personal
La comparación deja claro que los riesgos de seguridad son proporcionales a tres factores principales:  
- El valor de los datos que se manejan  
- La exposición a usuarios no confiables o a internet  
- La complejidad y las integraciones externas  

#### Autor

> **_Daniel Trujillo Martin_**