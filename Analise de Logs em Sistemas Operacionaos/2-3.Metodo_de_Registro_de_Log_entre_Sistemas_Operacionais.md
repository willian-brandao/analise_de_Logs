## Introdução 

Windows e Linux são dois sistemas operacionais amplamente usados, e cada um tem sua própria infraestrutura para gerar, guardar e consultar logs. Para analistas de segurança. entender as diferenças é fundamental para criar uma abordagem coersistiva para monitorar, detectar de ameaçar e responder incidentes. 

---

## Estruturas e Formatos Diferentes
|            Aspecto                   |             Linux                   |         Windows                              |
|--------------------------------------|-------------------------------------|----------------------------------------------|
| Formato de Logs                      |   Texto(syslog), CSV, JSON          | Binário (EVTX), XML (em algumas ferramentas) |
| Localização de Armazenamento         |   /var/log/                         | %SystemRoot%\System32\winevt\Logs\           |
| Método de acesso                     | Ferramentas de CLI (grep,journalctl | GUI(Event Viewer), Powershell                |
| Rotação de Logs                      | Gerenciamento por rotação de logs   | Sobrescrita automática ou arquivos manuais   |
| Timestamps                           | Legível por humanos / UTC           | UTC com contexto de tempo local              |
| Ferramentas de auditoria customizadas| auditd, syslog-ng, rsyslog          | Politicas de auditoria avançadas, sysmon     |

---

## Comparação de Registro de Logs 

|         Cenário                      |            Linux Log                                |        Windows Log                           |
|--------------------------------------|-----------------------------------------------------|----------------------------------------------|
| Login com Sucesso (local/SSH)        | Senha aceita por usuário com IP de origem           | 4624 (Login com sucesso )                    |
| Falha no Login                       | Senha falhou para usuário inválido com IP de origem | 4625 (Falha no Login)                        |


