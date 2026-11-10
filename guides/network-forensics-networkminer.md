# Análise Forense de Rede com NetworkMiner / Network Forensics with NetworkMiner

> **AVISO / WARNING**
> Executar apenas em laboratório isolado e com autorização. O uso em redes de terceiros é crime.
> Run only in an isolated lab with authorization. Using it on third-party networks is a crime.

## PORTUGUÊS

### 1. Objetivo
Utilizar o NetworkMiner para analisar capturas de tráfego (PCAP), extrair anfitriões, ficheiros, credenciais e reconstruir sessões em ambiente controlado.

### 2. Ferramentas
- NetworkMiner 3.1 (versão atual)
- Wireshark ou tcpdump (para captura)
- Máquina virtual Windows 10/11 ou Linux com Mono
- Servidor FTP e Samba de laboratório
- Ficheiro de captura exemplo: `ftp.pcap`

### 3. Introdução
O NetworkMiner é uma ferramenta de análise forense de rede (NFAT) passiva. Ao contrário de sniffers que apenas mostram pacotes, o NetworkMiner reconstrói sessões, extrai ficheiros transferidos, identifica sistemas operativos, credenciais e certificados. O fluxo de trabalho recomendado é capturar com Wireshark/tcpdump e analisar depois com NetworkMiner.

### 4. Pré-requisitos
- Descarregar o NetworkMiner 3.1 do site oficial: https://www.netresec.com/?page=NetworkMiner
- Instalar .NET Framework 4.7.2 ou superior (Windows) ou Mono (Linux)
- Garantir que a máquina de laboratório tem permissões de captura de pacotes

### 5. Tarefas

**Tarefa 1 — Instalação e primeira execução**
1. Descarregar o instalador ou o pacote portátil do site oficial.
2. Executar o `NetworkMiner.exe` (Windows) ou `mono NetworkMiner.exe` (Linux).
3. Confirmar que a interface principal abre corretamente.

**Tarefa 2 — Análise de captura FTP**
1. Abrir o ficheiro `ftp.pcap` no NetworkMiner (File > Open).
2. Na aba Hosts, identificar os anfitriões envolvidos.
3. Na aba Files, verificar os ficheiros transferidos.
4. Na aba Credentials, localizar utilizador e palavra-passe em texto claro.
5. Registar os resultados.

**Tarefa 3 — Captura em tempo real com Wireshark**
1. Iniciar captura no Wireshark na interface de laboratório.
2. Aceder ao servidor FTP de laboratório com um utilizador de teste.
3. Transferir um ficheiro pequeno.
4. Parar a captura e guardar como `ftp_lab.pcap`.
5. Abrir o ficheiro no NetworkMiner e repetir a análise da Tarefa 2.

**Tarefa 4 — Análise de tráfego Samba/SMB**
1. Capturar com Wireshark o acesso a uma partilha Samba de laboratório.
2. Transferir um ficheiro para o diretório TESTE.
3. Guardar a captura como `smb_lab.pcap`.
4. Abrir no NetworkMiner e verificar ficheiros e mensagens trocadas.

**Tarefa 5 — Análise de tráfego Web**
1. Capturar com Wireshark o acesso a um site de laboratório via HTTP.
2. Guardar a captura como `web_lab.pcap`.
3. Abrir no NetworkMiner e verificar pedidos, respostas, ficheiros e certificados.

**Tarefa 6 — Comparação e relatório**
1. Comparar os resultados das capturas FTP, SMB e Web.
2. Identificar que tipo de informação é exposta em cada protocolo.
3. Elaborar um relatório breve com os achados e medidas de mitigação.

### 6. Medidas de mitigação
- Utilizar protocolos criptografados: SFTP em vez de FTP, SMB sobre TLS, HTTPS em vez de HTTP.
- Segmentar a rede e aplicar controlo de acesso.
- Monitorizar tráfego com IDS/IPS.
- Formar utilizadores sobre riscos de protocolos em texto claro.

### 7. Referências
- Site oficial: https://www.netresec.com/?page=NetworkMiner
- Blog Netresec: https://www.netresec.com/?page=Blog
- Documentação: https://www.netresec.com/?page=Documentation
- Repositório: https://sourceforge.net/projects/networkminer/

---

## ENGLISH

### 1. Objective
Use NetworkMiner to analyze packet captures (PCAP), extract hosts, files, credentials, and reconstruct sessions in a controlled environment.

### 2. Tools
- NetworkMiner 3.1 (current version)
- Wireshark or tcpdump (for capture)
- Windows 10/11 virtual machine or Linux with Mono
- Lab FTP and Samba servers
- Sample capture file: `ftp.pcap`

### 3. Introduction
NetworkMiner is a passive network forensic analysis tool (NFAT). Unlike packet sniffers, it reconstructs sessions, extracts transferred files, identifies operating systems, credentials, and certificates. The recommended workflow is to capture with Wireshark/tcpdump and analyze afterwards with NetworkMiner.

### 4. Prerequisites
- Download NetworkMiner 3.1 from the official site: https://www.netresec.com/?page=NetworkMiner
- Install .NET Framework 4.7.2 or later (Windows) or Mono (Linux)
- Ensure the lab machine has packet capture permissions

### 5. Tasks

**Task 1 — Installation and first run**
1. Download the installer or portable package from the official site.
2. Run `NetworkMiner.exe` (Windows) or `mono NetworkMiner.exe` (Linux).
3. Confirm the main interface opens correctly.

**Task 2 — FTP capture analysis**
1. Open `ftp.pcap` in NetworkMiner (File > Open).
2. In the Hosts tab, identify the involved hosts.
3. In the Files tab, check transferred files.
4. In the Credentials tab, locate cleartext username and password.
5. Record the results.

**Task 3 — Live capture with Wireshark**
1. Start a capture in Wireshark on the lab interface.
2. Access the lab FTP server with a test user.
3. Transfer a small file.
4. Stop the capture and save as `ftp_lab.pcap`.
5. Open the file in NetworkMiner and repeat the Task 2 analysis.

**Task 4 — Samba/SMB traffic analysis**
1. Capture Samba share access with Wireshark.
2. Transfer a file to the TESTE directory.
3. Save the capture as `smb_lab.pcap`.
4. Open in NetworkMiner and check exchanged files and messages.

**Task 5 — Web traffic analysis**
1. Capture HTTP access to a lab website with Wireshark.
2. Save the capture as `web_lab.pcap`.
3. Open in NetworkMiner and check requests, responses, files, and certificates.

**Task 6 — Comparison and report**
1. Compare results from FTP, SMB, and Web captures.
2. Identify what information is exposed in each protocol.
3. Write a short report with findings and mitigation measures.

### 6. Mitigation measures
- Use encrypted protocols: SFTP instead of FTP, SMB over TLS, HTTPS instead of HTTP.
- Segment the network and enforce access control.
- Monitor traffic with IDS/IPS.
- Train users on the risks of cleartext protocols.

### 7. References
- Official site: https://www.netresec.com/?page=NetworkMiner
- Netresec blog: https://www.netresec.com/?page=Blog
- Documentation: https://www.netresec.com/?page=Documentation
- Repository: https://sourceforge.net/projects/networkminer/
