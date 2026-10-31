# windows-security-log-investigation

# Windows Security Log Investigation

**Proyecto:** Blue Team / SOC Analyst  
**Herramientas:** Windows Event Viewer y PowerShell  
**Entorno:** Equipo Windows personal  
**Tipo:** Investigación de laboratorio con registros reales  
**Fecha:** Octubre de 2026

## 1. Objetivo

Analizar eventos de seguridad de Windows para identificar tipos de autenticación, clasificar accesos exitosos y fallidos, e investigar posibles comportamientos sospechosos.

## 2. Metodología

Se consultó el registro Security de Windows mediante PowerShell, utilizando Get-WinEvent para extraer eventos de autenticación.

Se examinaron los identificadores 4624 y 4625, los tipos de inicio de sesión, los códigos de estado y los procesos asociados.

## 3. Resultados

**Autenticaciones exitosas (Event ID 4624)**

Se identificaron inicios de sesión de servicios mediante la cuenta SYSTEM (Logon Type 5), además de autenticaciones interactivas locales (Logon Type 2).

**Autenticaciones fallidas (Event ID 4625)**

Se analizaron 20 eventos fallidos registrados entre el 21 y el 27 de octubre de 2026.

Diez eventos examinados en detalle presentaron el código de estado 0xC000006E, asociado a restricciones de cuenta.

En cinco de estos eventos se identificaron los siguientes procesos:

- Google Chrome: 1 evento.
- Microsoft Edge WebView2: 4 eventos.

## 4. Evaluación de seguridad

Los eventos analizados no proporcionan evidencia suficiente para confirmar actividad maliciosa.

No se ha determinado la causa específica de las restricciones de cuenta ni se ha establecido que los procesos observados estuvieran comprometidos.

## 5. Recomendaciones

- Correlacionar los fallos con la actividad habitual del usuario.
- Comprobar la legitimidad de los ejecutables involucrados si aparecen otros indicadores sospechosos.
- Mantener actualizados Windows y los navegadores.
- Conservar los registros relevantes para futuras investigaciones.

## 6. Conclusión

El proyecto demuestra el uso de herramientas nativas de Windows para investigar eventos de autenticación, interpretar códigos de error y documentar hallazgos basados en evidencias.

**Resultado:** no se confirmó ningún incidente de seguridad dentro del conjunto de eventos analizado.

## 7. Limitaciones

El análisis se realizó sobre una selección de eventos de un único equipo. No constituye una auditoría de seguridad integral ni permite descartar amenazas no observadas.
