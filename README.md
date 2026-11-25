\# Actividad 2.18 — Seguridad en el SDLC



Este repositorio implementa controles de seguridad automatizados dentro del ciclo de vida del desarrollo de software.



\## Herramientas utilizadas



\- \*\*GitHub Actions\*\*: ejecuta el pipeline automáticamente.

\- \*\*Semgrep\*\*: realiza análisis estático de seguridad del código (SAST).

\- \*\*Trivy\*\*: analiza dependencias y detecta vulnerabilidades conocidas.

\- \*\*GitHub Issues\*\*: se utiliza como sistema de seguimiento de tickets.



\## Funcionamiento del pipeline



Cada vez que se realiza un `push` a la rama `main` o se abre un pull request:



1\. Se ejecuta un análisis SAST con Semgrep.

2\. Se escanean las dependencias del proyecto con Trivy.

3\. Se generan reportes en formato SARIF.

4\. Si se detecta una vulnerabilidad crítica, se crea automáticamente un issue.

5\. El despliegue simulado solo se ejecuta si no hay errores de seguridad.



\## Control de despliegue



El job `deploy` está configurado para ejecutarse únicamente si los análisis de seguridad anteriores finalizan correctamente.



Si Trivy detecta una vulnerabilidad crítica o alta, el pipeline falla, se crea un ticket y el despliegue queda bloqueado.

