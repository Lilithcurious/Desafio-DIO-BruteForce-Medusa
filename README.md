Desafio DIO - Simulação de Ataques com Kali Linux e Metasploitable

Introdução
Este projeto é parte do desafio da DIO para explorar conceitos de cibersegurança, utilizando Kali Linux e Metasploitable 2 em um ambiente virtual controlado. O objetivo é simular ataques de força bruta com a ferramenta Medusa, documentar o processo e propor medidas de mitigação, demonstrando aprendizado prático em segurança.

Configuração do Ambiente
Ferramentas Utilizadas: Kali Linux (versão mais recente), VirtualBox, Metasploitable 2, Medusa, Nmap.
Setup: Duas máquinas virtuais foram configuradas com rede interna (host-only) para simulações seguras. A VM Kali serve como estação de ataque, enquanto a Metasploitable atua como alvo vulnerável.

Passos Iniciais:

Importei as imagens .ova do Kali e Metasploitable no VirtualBox.
Configurei a rede como "Host-Only Adapter" para isolar o ambiente.
Iniciei as VMs e confirmei conectividade com ping e verificação de IPs via ifconfig.
Testes Realizados
Enumeração de Serviços
Utilizei o Nmap para mapear serviços abertos no alvo Metasploitable:
Comando: nmap -sV <alvo>
Resultados: Identifiquei portas como 21 (FTP), 80 (HTTP), e 445 (SMB), indicando serviços vulneráveis para testes.

Observação: O scan levou cerca de 26 segundos e revelou uma versão desatualizada do vsftpd, típica do Metasploitable 2.

Ataque de Força Bruta com Medusa
Testei um ataque de força bruta no serviço FTP do Metasploitable:
Comando: medusa -h <alvo> -u user -P /usr/share/wordlists/rockyou.txt -M ftp
Configuração: Usei a wordlist padrão rockyou.txt e o módulo FTP do Medusa.
Resultado: O ataque foi interrompido devido a um erro de login, indicando necessidade de ajustes (ex.: verificar credenciais ou permissões).
Validação: Tentei acessar o FTP manualmente com ftp <alvo>, mas o teste foi inconclusivo por enquanto.

Evidências
Capturas de tela dos comandos Nmap e Medusa estão disponíveis na pasta /images/.
Arquivos de wordlists personalizadas e logs (com senhas redigidas) estão em /wordlists/.

Reflexões e Próximos Passos

Aprendizado: Entendi a importância da enumeração inicial com Nmap para identificar alvos e a flexibilidade do Medusa para diferentes serviços.
Desafios: O erro no Medusa sugere que devo verificar a sintaxe ou criar uma wordlist mais específica.

Próximos Passos:

Ajustar o comando Medusa e retomar o ataque FTP.
Configurar o DVWA no Metasploitable e simular força bruta em formulários web.
Explorar password spraying em SMB e documentar recomendações de mitigação.

Mitigações Propostas
Usar senhas fortes e complexas com políticas de expiração.
Implementar rate limiting (ex.: fail2ban) para bloquear tentativas excessivas.
Manter softwares e serviços atualizados para evitar explorações de versões conhecidas.

Recursos Utilizados
Kali Linux - Site Oficial
Metasploitable 2 - Rapid7
Medusa - Documentação
