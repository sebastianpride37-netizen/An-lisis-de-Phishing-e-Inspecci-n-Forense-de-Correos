[INFORME TECNICO ANALISIS DE PHISHING.md](https://github.com/user-attachments/files/33319467/INFORME.TECNICO.ANALISIS.DE.PHISHING.md)
# 📧 Email Forensic Analysis & Phishing Investigation | Enterprise SOC Lab

![Security Analyst](https://img.shields.io/badge/Role-SOC_Analyst_Tier_1-blue?style=for-the-badge&logo=siem)
![Platform](https://img.shields.io/badge/Environment-Linux_Sandbox-orange?style=for-the-badge&logo=linux)
![Framework](https://img.shields.io/badge/Framework-NIST_SP_800--61_|_MITRE_ATT%26CK-red?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)

> **Investigación forense de artefactos de correo electrónico, inspección de cabeceras SMTP, extracción de archivos Base64 vía CLI Linux y sanitización de Indicadores de Compromiso (IOCs).**

---

## 📌 Executive Summary (Resumen Ejecutivo)

En el monitoreo continuo de un **Centro de Operaciones de Seguridad (SOC)**, el correo electrónico representa el vector de ataque perimetral más explotado por los actores de amenaza. 

Este proyecto documenta la investigación técnica y el análisis forense de archivos de correo sin procesar (`.eml` / `.txt`). El objetivo principal consistió en desglosar las tres capas del mensaje (cabeceras, cuerpo HTML y adjuntos), identificar técnicas de ingeniería social, decodificar *payloads* codificados en Base64 utilizando la línea de comandos en Linux (`bash`) y aplicar metodologías estándar de neutralización (*defanging*) para el reporte seguro de incidentes.

---

## 🎯 Scope & Threat Taxonomy (Taxonomía de Amenazas)

Durante este análisis se evaluaron y categorizaron las siguientes tipologías de correo malicioso y vectores de ataque:

* **Spam / Malspam:** Envíos masivos no solicitados con o sin carga útil maliciosa.
* **Phishing & Brand Impersonation:** Suplantación de identidad para captura de credenciales o datos financieros.
* **Spear Phishing & Whaling:** Ataques personalizados dirigidos a individuos específicos o alta dirección (CEO/CFO).
* **Business Email Compromise (BEC):** Compromiso de cuentas corporativas para fraude financiero.
* **Smishing / Vishing:** Desplazamiento del vector de engaño hacia SMS o ingeniería social por voz.

---

## 🛠️ Tools & Technologies Used

| Categoria | Herramientas / Tecnologías |
| :--- | :--- |
| **Operating System** | Linux Sandbox / Ubuntu VM (CLI Focus) |
| **Text & Log Parsing** | `grep`, `tail`, `pipeline (|)`, `xdg-open` |
| **Decoding & Forensic Tools** | `base64` utility, MIME Parsers |
| **Email Protocols** | SMTP, POP3, IMAP |
| **Authentication Protocols** | SPF (Sender Policy Framework), DKIM, DMARC |

---

## 🔍 Investigation Methodology & Step-by-Step Execution

El análisis forense se ejecutó en tres niveles lógicos directamente desde la consola Bash de Linux para prevenir riesgos de ejecución accidental en la interfaz gráfica.
