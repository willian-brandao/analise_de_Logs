# O que são logs

Na operações de cibersegurança, especialmente na perspectiva do Blue Team, os logs são fundamentais para visibilidade, monitoramento e respostas. Eles representam as pegadas de tudo que acontece nos sistemas, aplicações e redes. Sem o registro e logs, detectar comportamentos anormais ou monitorar atividades maliciosas se tornaria quase impossível.

Um log é um registro de data/hora gerada por sistemas, aplicações, serviços, dispositivos ou ferramenta de segurança. Logs documentam eventos como autenticação de usuário, execução de processos, conexões de internet, acesso a arquivos, mudanças de configuração, erros de sistemas ou violações de políticas de segurança.

## Tipos de Logs

| Origem                       | Exemplo de Log    | Caso de uso em Blue Team                                                               |
|------------------------------|-------------------|----------------------------------------------------------------------------------------| 
| Sistema Operacional (linux)  | /var/log/auth.log | Tentativas de login via SSH, Uso com privilégio de admin                               |
| Sitema Operacional (Windows) | Security.evtx     | Logins, criação de processos, uso com privilégios de admin                             | 
| Dispositivos de Rede         | Logs de Firewall<br> Logs DHCP | Bloqueio de tráfego, alocação de endereços                                |
| Servidores Web               | Apache, Acesso ao Nginx/logs de erro| URIs Suspeitas, 404 fuzzing, travessia de diretório                  |
| Ferramentas de Segurança     | EDR, Antivirus, Logs de SIEM | Detecção de Ameaças, movimento lateral                                      |
| Infraestrutura de Nuvem      | AWS Cloudtrail, Logs de atividade do Azure | uso indevido de api, tentativa de provilégio de escalonamento |

## Eventos vs Logs

* Eventos - uma instância única ou uma ação, exemplo: "usuário admin está logado".
* Logs - Um registro escrito de um evento, possivelmente estruturado em JSON ou sem estrutura em arquivo de texto.

Todo log contém, pelo menos, um registro de tempo, o sistema de origem, e a descrição do evento. Campos adicionais dependem do software/hardware que vai gerar o log.

## Exemplos de Entradas de Logs

### 1. Falha de Autenticação de SSH no Linux
<img width="908" height="52" alt="image" src="https://github.com/user-attachments/assets/656ab133-902e-4b37-8e6d-277bb2670909" />

* Interpretação - O sistema rejeitou uma tentativa de autenticação para o usuário root conectado no IP 192.168.1.23.
* Caso de uso - Correlação de múltiplas tentativas falhas de logins para detectar atividade de força bruta.

### 2. Evento de login no Windows ( Security.evtx, Event ID 4624)
<img width="898" height="129" alt="image" src="https://github.com/user-attachments/assets/a5474282-1d2b-478b-b461-5f110eae62eb" />

* Interpretação: Um login bem sucedido realizado via RDP do IP 10.0.0.4 por uma conta de administrador.
* Caso de uso: Detecção de acesso RDP não autorizado ou movimento lateral.

### 3. Log de acesso a servidor web 

<img width="770" height="58" alt="image" src="https://github.com/user-attachments/assets/71c6fbce-8991-4d1f-8f4f-9ac0c3a9c731" />

* Interpretação: Cliente alocado no IP 192.168.1.50 tentou acessar uma área restrita (/admin) e recebeu um erro 401 desautorizando.
* Caso de Uso 
