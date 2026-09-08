# 🛡️ Seguridad en Active Directory — Simulación Red Team vs Blue Team

Trabajo Fin de Máster — Programa Profesional en Ciberseguridad (UNIR)

## 📋 Resumen

Laboratorio práctico de ataque y defensa sobre una infraestructura de **Active Directory** virtualizada, simulando un entorno corporativo realista. El proyecto cubre el ciclo completo: desde el reconocimiento inicial hasta el compromiso total del dominio, y su correspondiente detección y mitigación desde la perspectiva defensiva.

📄 **[Ver memoria completa (PDF)](./Seguridad_En_Active_Directory.pdf)**

## 🎯 Objetivo

Evaluar la resiliencia de un entorno de Active Directory mediante un ejercicio de Red Team / Blue Team, usando exclusivamente herramientas de código abierto, y proponer medidas de bastionado basadas en los resultados.

## 🧪 Entorno del laboratorio

| Nodo | Sistema operativo | Rol |
|---|---|---|
| Controlador de Dominio | Windows Server 2019 | Núcleo de identidad (AD) |
| Estación de trabajo | Windows 10 Pro | Equipo víctima unido al dominio |
| Máquina atacante | Kali Linux | Ejecución de la fase ofensiva |
| Servidor de seguridad | Ubuntu Server | SIEM (Wazuh) + IDS (Suricata) |

## ⚔️ Fase ofensiva (Red Team)

- **Reconocimiento:** escaneo de puertos y servicios con **Nmap**
- **Acceso inicial:** ataque de fuerza bruta sobre SMB con **Hydra**
- **Post-explotación:** extracción de credenciales del dominio (DCSync) con **Impacket**
- **Ejecución remota:** control total del sistema mediante **Metasploit** (módulo psexec)

## 🔍 Fase defensiva (Blue Team)

- **SIEM:** Wazuh, para ingesta, correlación y visualización de eventos
- **IDS de red:** Suricata, detección de tráfico malicioso en tiempo real
- **Telemetría de endpoint:** Microsoft Sysmon, con configuración basada en el estándar SwiftOnSecurity
- **Auditoría avanzada:** políticas de grupo (GPO) para registrar eventos críticos de Active Directory (inicios de sesión, replicación de directorio, creación de procesos)

Todos los ataques ejecutados fueron detectados por el SIEM en menos de 5 segundos.

## 🛠️ Propuestas de mejora

- Restricción y auditoría del protocolo NTLM
- Mitigación de DCSync mediante restricción de permisos de replicación (DACL)
- Hardening de PowerShell con Constrained Language Mode y AppLocker

## 📚 Marcos de referencia utilizados

MITRE ATT&CK · Cyber Kill Chain

## 🔑 Palabras clave

`Active Directory` `Wazuh` `Suricata` `Kerberos` `Metasploit` `Nmap` `Red Team` `Blue Team` `SIEM`

---

**Autor:** Marcos Torri Fernández — [GitHub](https://github.com/MarcosTorri) · [LinkedIn](https://www.linkedin.com/in/marcos-torri-fern%C3%A1ndez-533860348/)
