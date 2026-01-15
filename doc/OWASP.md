# **OWASP Top 10 – 2025**

El **OWASP Top 10** es una lista de los riesgos de seguridad más críticos en aplicaciones web, actualizada regularmente para reflejar las amenazas actuales. La versión 2025 presenta cambios importantes respecto a años anteriores, priorizando problemas de diseño, integridad del software y fallos en la cadena de suministro.

- [**OWASP Top 10 – 2025**](#owasp-top-10--2025)
  - [**A01:2025 – Broken Access Control (Control de Acceso Roto)**](#a012025--broken-access-control-control-de-acceso-roto)
  - [**A02:2025 – Security Misconfiguration (Mala Configuración de Seguridad)**](#a022025--security-misconfiguration-mala-configuración-de-seguridad)
  - [**A03:2025 – Software Supply Chain Failures (Fallos en la Cadena de Suministro de Software)**](#a032025--software-supply-chain-failures-fallos-en-la-cadena-de-suministro-de-software)
  - [**A04:2025 – Cryptographic Failures (Fallos Criptográficos)**](#a042025--cryptographic-failures-fallos-criptográficos)
  - [**A05:2025 – Injection (Inyección)**](#a052025--injection-inyección)
  - [**A06:2025 – Insecure Design (Diseño Inseguro)**](#a062025--insecure-design-diseño-inseguro)
  - [**A07:2025 – Authentication Failures (Fallos de Autenticación)**](#a072025--authentication-failures-fallos-de-autenticación)
  - [**A08:2025 – Software or Data Integrity Failures (Fallos de Integridad de Software o Datos)**](#a082025--software-or-data-integrity-failures-fallos-de-integridad-de-software-o-datos)
  - [**A09:2025 – Security Logging and Alerting Failures (Fallos de Registro y Alerta de Seguridad)**](#a092025--security-logging-and-alerting-failures-fallos-de-registro-y-alerta-de-seguridad)
  - [**A10:2025 – Mishandling of Exceptional Conditions (Manejo Incorrecto de Condiciones Excepcionales)**](#a102025--mishandling-of-exceptional-conditions-manejo-incorrecto-de-condiciones-excepcionales)
  - [**Conclusión**](#conclusión)

---

## **A01:2025 – Broken Access Control (Control de Acceso Roto)**

**Qué es:**
Ocurre cuando un usuario puede acceder a funciones o datos que no debería, por ejemplo, modificando URLs o usando privilegios de otro usuario.

**Ejemplo:**
Un usuario normal puede cambiar su rol a administrador mediante la URL:
`/admin/deleteUser?id=123`

**Cómo mitigarlo:**

* Implementar controles de acceso en el servidor, no solo en la interfaz.
* Usar listas de control de acceso (ACL) y políticas basadas en roles.
* Revisar todas las rutas y funciones sensibles.

---

## **A02:2025 – Security Misconfiguration (Mala Configuración de Seguridad)**

**Qué es:**
Cuando un sistema tiene configuraciones inseguras que facilitan ataques, como puertos abiertos, servicios innecesarios o errores de permisos.

**Ejemplo:**
Un servidor web expone directorios sensibles sin autenticación:
`http://midominio.com/.git/`

**Cómo mitigarlo:**

* Configurar correctamente servidores, bases de datos y frameworks.
* Eliminar servicios y puertos innecesarios.
* Aplicar actualizaciones y parches regularmente.

---

## **A03:2025 – Software Supply Chain Failures (Fallos en la Cadena de Suministro de Software)**

**Qué es:**
Riesgos introducidos por dependencias externas, librerías o componentes de terceros que contienen vulnerabilidades.

**Ejemplo:**
Una librería NPM utilizada tiene un malware que roba datos de usuarios.

**Cómo mitigarlo:**

* Usar repositorios confiables y firmados.
* Revisar vulnerabilidades en dependencias con herramientas de análisis.
* Mantener actualizadas todas las librerías y componentes.

---

## **A04:2025 – Cryptographic Failures (Fallos Criptográficos)**

**Qué es:**
El mal uso de criptografía que permite que los datos sensibles sean accesibles por atacantes.

**Ejemplo:**
Guardar contraseñas en texto plano en la base de datos.

**Cómo mitigarlo:**

* Usar algoritmos fuertes y modernos (AES, RSA, SHA-256).
* Nunca almacenar contraseñas sin hash y salt.
* Cifrar datos sensibles en tránsito y en reposo.

---

## **A05:2025 – Injection (Inyección)**

**Qué es:**
Ocurre cuando datos no confiables se envían a un intérprete como SQL, LDAP o comandos de sistema, permitiendo manipular el comportamiento de la aplicación.

**Ejemplo:**
SQL Injection:

```sql
SELECT * FROM usuarios WHERE nombre = ' " + usuario + " ';
```

**Cómo mitigarlo:**

* Usar consultas parametrizadas o prepared statements.
* Validar y sanear entradas del usuario.
* Evitar concatenar directamente datos de entrada en comandos.

---

## **A06:2025 – Insecure Design (Diseño Inseguro)**

**Qué es:**
Errores de diseño de la aplicación que crean vulnerabilidades, incluso antes de codificar.

**Ejemplo:**
No definir roles y permisos correctamente desde el diseño, lo que permite acceso indebido a funciones.

**Cómo mitigarlo:**

* Aplicar principios de seguridad desde el diseño (“security by design”).
* Realizar revisiones de arquitectura y threat modeling.
* Considerar la seguridad en cada decisión de diseño.

---

## **A07:2025 – Authentication Failures (Fallos de Autenticación)**

**Qué es:**
Problemas al verificar la identidad de los usuarios, permitiendo suplantaciones.

**Ejemplo:**
Permitir contraseñas débiles o reutilización de sesiones sin expiración.

**Cómo mitigarlo:**

* Usar autenticación multifactor (MFA).
* Aplicar políticas de contraseñas seguras.
* Expirar tokens y sesiones correctamente.

---

## **A08:2025 – Software or Data Integrity Failures (Fallos de Integridad de Software o Datos)**

**Qué es:**
La aplicación o los datos pueden ser modificados maliciosamente sin que se detecte.

**Ejemplo:**
Una actualización de software descargada desde una fuente no confiable contiene malware.

**Cómo mitigarlo:**

* Firmar digitalmente actualizaciones y paquetes de software.
* Validar integridad de datos críticos y usar checksums.
* Monitorear cambios inesperados en sistemas y bases de datos.

---

## **A09:2025 – Security Logging and Alerting Failures (Fallos de Registro y Alerta de Seguridad)**

**Qué es:**
No registrar correctamente eventos importantes de seguridad o no alertar ante incidentes.

**Ejemplo:**
No registrar intentos fallidos de inicio de sesión, lo que impide detectar ataques de fuerza bruta.

**Cómo mitigarlo:**

* Implementar logs detallados de seguridad.
* Configurar alertas automáticas para eventos críticos.
* Revisar regularmente los registros para detectar anomalías.

---

## **A10:2025 – Mishandling of Exceptional Conditions (Manejo Incorrecto de Condiciones Excepcionales)**

**Qué es:**
Errores al gestionar situaciones inesperadas, lo que puede exponer información o interrumpir servicios.

**Ejemplo:**
Mostrar mensajes de error detallados con rutas de archivos o información de la base de datos.

**Cómo mitigarlo:**

* Gestionar excepciones y errores de forma controlada.
* Evitar exponer información sensible en mensajes de error.
* Registrar internamente errores para análisis sin mostrar datos críticos al usuario.

---

## **Conclusión**

El OWASP Top 10 – 2025 destaca cómo la seguridad debe ser considerada **desde el diseño hasta el mantenimiento**. Los ataques modernos no solo aprovechan fallos técnicos, sino también errores en la gestión, diseño y cadena de suministro de software. Aplicar buenas prácticas y mantener las aplicaciones actualizadas reduce significativamente los riesgos.
