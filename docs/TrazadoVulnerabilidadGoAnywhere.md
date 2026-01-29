# Trazado de Vulnerabilidad
La vulnerabilidad que yo escogi es la `CVE-2024-0204`

![Vulnerabilidad ](https://raw.githubusercontent.com/vjp-danielTM/PPSUnidad2-TrazadoVulnerabilidad/refs/heads/main/capturas/1.png)

Si nos metemos en el enlace que  nos da incibe nos lleva a la siguiente pagina que sale una descripcion de la vulnerabilidad y la gravedad que tiene 

![Vulnerabilidad Descripcion](https://raw.githubusercontent.com/vjp-danielTM/PPSUnidad2-TrazadoVulnerabilidad/refs/heads/main/capturas/2.png)

Despues con el CVE que tenemos en la pagina de NVD miramos la criticidad y el vector de la vulnerabilidad

![NVD](https://raw.githubusercontent.com/vjp-danielTM/PPSUnidad2-TrazadoVulnerabilidad/refs/heads/main/capturas/3.png)

Si ponemos el raton encima del vector te sale una descripcion de las metricas que usaron para calcular el porque de esa puntuacion

![Vector NVD](https://raw.githubusercontent.com/vjp-danielTM/PPSUnidad2-TrazadoVulnerabilidad/refs/heads/main/capturas/4.png)

Si bajamos  un poco podemos ver que tambien sale el CWE que son las debilidades que son explotadas por esta vulnerabilidad 


![CWE](https://raw.githubusercontent.com/vjp-danielTM/PPSUnidad2-TrazadoVulnerabilidad/refs/heads/main/capturas/5.png)

Aqui podemos ver la descripcion de la vulnerabilidad [CWE-425](https://cwe.mitre.org/data/definitions/425.html).

![CWE](https://raw.githubusercontent.com/vjp-danielTM/PPSUnidad2-TrazadoVulnerabilidad/refs/heads/main/capturas/6.png)

> Es una debilidad en aplicaciones web donde no se verifica correctamente la autorización en todas las URLs, scripts o archivos restringidos. La aplicación asume que los recursos sensibles solo se acceden a través de una ruta "normal" (por ejemplo, un menú o enlace protegido), pero un atacante puede acceder directamente escribiendo o adivinando la URL completa, saltándose los controles de autenticación o autorización.


Aqui tambien podemos encontrar como mitigarlo.

![CWE Mitigacion](https://raw.githubusercontent.com/vjp-danielTM/PPSUnidad2-TrazadoVulnerabilidad/refs/heads/main/capturas/7.png)


Tambien tenemos los CAPEC que son la `enumeración` y `clasificación` común de patrones de ataque es decir forma estandarizada los patrones de ataque comunes que usan los adversarios para explotar debilidades.

### El primero es CAPEC-127: Directory Indexing
Un atacante envía una solicitud que fuerza al servidor a listar/indexar el contenido de un directorio. Esto revela archivos sensibles, backups, configs o directorios ocultos que no deberían ser visibles.

![CAPEC-127](https://raw.githubusercontent.com/vjp-danielTM/PPSUnidad2-TrazadoVulnerabilidad/refs/heads/main/capturas/8.png)

### El segundo CAPEC-143: Detect Unpublicized Web Pages
El atacante busca y detecta páginas web no publicadas o no enlazadas en el sitio. Usa spidering, adivinanza de URLs predecibles o herramientas para mapear el sitio y encontrar recursos no indexados.

![CAPEC-143](https://raw.githubusercontent.com/vjp-danielTM/PPSUnidad2-TrazadoVulnerabilidad/refs/heads/main/capturas/9.png)

### El tercero CAPEC-144: Detect Unpublicized Web Services
Similar al anterior, pero enfocado en servicios web no publicados. El atacante descubre y explora servicios web no documentados o no enlazados públicamente mediante escaneo, WSDL guessing o patrones comunes.

![CAPEC-144](https://raw.githubusercontent.com/vjp-danielTM/PPSUnidad2-TrazadoVulnerabilidad/refs/heads/main/capturas/9.1.png)

### El cuarto CAPEC-668: Key Negotiation of Bluetooth Attack (KNOB)
Ataque específico contra Bluetooth Classic. El atacante manipula la negociación de claves de cifrado para forzar una clave de baja entropía, permitiendo brute-force en tiempo real y descifrar tráfico. Afecta dispositivos que negocian claves sin proteger la integridad del proceso.

![CAPEC-668](https://raw.githubusercontent.com/vjp-danielTM/PPSUnidad2-TrazadoVulnerabilidad/refs/heads/main/capturas/10.png)

### El quinto CAPEC-87: Forceful Browsing (también conocido como Forced Browsing o Direct Request)
El atacante accede directamente a URLs o recursos restringidos escribiéndolos manualmente. Permite llegar a secciones administrativas, archivos sensibles o funcionalidades privilegiadas que deberían estar protegidas por autenticación/autorización, pero no lo están en cada solicitud.

![CAPEC-87](https://raw.githubusercontent.com/vjp-danielTM/PPSUnidad2-TrazadoVulnerabilidad/refs/heads/main/capturas/11.png)


Tambien podemos descargar el registro de la vulnerabilidad en json

![CVE.ORG](https://raw.githubusercontent.com/vjp-danielTM/PPSUnidad2-TrazadoVulnerabilidad/refs/heads/main/capturas/12.png)

![JSON CVE](https://raw.githubusercontent.com/vjp-danielTM/PPSUnidad2-TrazadoVulnerabilidad/refs/heads/main/capturas/13.png)

#### Autor

> **_Daniel Trujillo Martin_**