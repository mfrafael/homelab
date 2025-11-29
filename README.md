# ⚙️ Documentação do Homelab: Mini PC Beelink S13

[![Status](https://img.shields.io/badge/Status-Ativo-brightgreen)]() [![Proxmox](https://img.shields.io/badge/Hypervisor-Proxmox%20VE-orange)]() [![Debian](https://img.shields.io/badge/OS-Debian%2013-red)]()

Esta documentação detalha o inventário físico, configurações de rede e serviços virtuais (Proxmox LXC/VMs) do Homelab.

> 🔐 **Credenciais:** Todas as credenciais, senhas e tokens sensíveis estão armazenados no arquivo **`CREDENTIALS.md`** (não incluído no git). Consulte esse arquivo para acessar cada serviço.

## 📋 Índice Rápido

- [Inventário Físico](#1-inventário-físico-e-sistema-base)
- [Arquitetura do Homelab](#2-arquitetura-do-homelab-diagrama-visual)
- [Configurações de Rede](#3-configurações-de-rede-lógicas-lan)
- [Serviços Virtuais](#4-serviços-virtuais-vms-e-lxcs)
- [Armazenamento](#5-gerenciamento-e-compartilhamento-de-armazenamento)
- [DNS & Rede](#7-dns-e-configurações-de-rede-detalhadas)
- [Monitoramento](#8-monitoramento)
- [Segurança](#12-segurança-e-boas-práticas)

---

## 1. Inventário Físico e Sistema Base

### 1.1 Servidor Principal (Hypervisor)

| Descrição | Detalhe | Observações |
| :--- | :--- | :--- |
| **Nome/Função** | Servidor Proxmox VE (Hypervisor) | Ponto central do Homelab. |
| **Modelo** | Beelink Mini S13 | Mini PC compacto (115 x 110 x 40mm). |
| **CPU** | Intel Processor N150 | |
| **RAM** | 16 GB LPDDR4 | |
| **Armazenamento (Local)** | 512GB PCIe 3 SSD | Usado para o Proxmox OS, VMs, LXCs e Storages locais. |
| **Sistema Operacional** | **Proxmox VE** (Base: **Debian 13 "Trixie"**) | Versão estável do Debian. |
| **IP (Gerenciamento)** | `192.168.0.88:8006` | Acesso à WebUI do Proxmox. |
| **Comportamento de Energia** | **Auto-inicialização na BIOS** | Liga automaticamente após queda de energia. |

### 1.2 Armazenamento Externo (Dados e Mídia)

Este é o disco de armazenamento principal para dados de mídia, downloads e arquivos grandes.

| Descrição | Detalhe | Status |
| :--- | :--- | :--- |
| **Modelo/Família** | Seagate Exos (ST24000NM000H-3KS103) | Classe Enterprise/Data Center (24/7). |
| **Capacidade** | 24.0 TB | Dobro da capacidade anterior (12 TB). |
| **Serial Number** | ZYD0CB2X | |
| **Firmware** | SN04 | |
| **Velocidade de Rotação** | 7200 RPM | |
| **Tamanho Físico** | 3.5 polegadas | |
| **Interface SATA** | SATA 3.3, 6.0 Gb/s | Conexão completa. |
| **Setores** | 512B lógico, 4096B físico | |
| **Dispositivo Linux** | `/dev/sda` | |
| **Ponto de Montagem** | `/mnt/externalhdd` | Configurado para montagem automática. |
| **SMART Status** | ✅ Ativo & Disponível | Health Test: PASSED |


#### 1.2.1 Case Externo (ORICO)

O HDD está instalado em um case externo ORICO com as seguintes especificações:

| Característica | Detalhe |
| :--- | :--- |
| **Interface** | USB 3.0 com UASP (5 Gbps) |
| **Alimentação** | Fonte externa 12V (até 24W) |
| **Material** | Liga de alumínio e ABS |
| **Design** | Vertical com LED indicador |
| **Conexão HDD** | SATA III |
| **Compatibilidade** | Windows, Mac OS e Linux |
| **Refrigeração** | Dissipação passiva através do corpo em alumínio |

**Kit Inclui:**
- Case ORICO USB3.0/SATA III
- Dock destacável
- Fonte de alimentação 12V
- Cabo USB 3.0 (Tipo B)
- Kit de instalação (chave de fenda e parafusos)

---

## 2. Arquitetura do Homelab (Diagrama Visual)

![Diagrama da Arquitetura do Homelab](./diagram.svg)

---

## 3. Configurações de Rede Lógicas (LAN)

### 3.1 Esquema de Endereçamento

| Função | Dispositivo | Endereço IP | Sub-rede / Observações |
| :--- | :--- | :--- | :--- |
| **Modem ISP** | Modem | `192.168.1.1` | Recebe o sinal de Internet. |
| **Roteador Principal (WAN)** | Roteador | `192.168.1.2` | Conexão com o Modem ISP. |
| **Roteador Principal (LAN)** | Roteador | **`192.168.0.1`** | **Gateway da LAN principal** (`192.168.0.0/24`). |
| **Servidor Proxmox** | Mini PC S13 | **`192.168.0.88`** | IP principal do host. |

### 3.2 Política de IPs

* **Política de IP:** IPs Estáticos/Reservados para todos os serviços listados.
* **Máscara de Sub-rede:** `/24` (255.255.255.0)
* **Range:** `192.168.0.1` - `192.168.0.254`

> 🔐 **Credenciais:** Ver arquivo `CREDENTIALS.md` (não está no git)

---

## 4. Serviços Virtuais (VMs e LXCs)

Esta tabela lista todos os serviços em execução no Proxmox, seus acessos e configurações especiais.

| ID | Nome do Serviço | Tipo | Endereço IP / Acesso | Porta(s) | Status | Anotações |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **100** | **HomeAssistant** | VM | `http://homeassistant.local:8123/` | `8123` | ✅ Ativo | Automação residencial (VM). |
| **101** | Adguard | LXC | `http://192.168.0.52` | 53, 80 | ✅ Ativo | Filtro de DNS (bloqueio de anúncios). |
| **102** | Jellyfin | LXC | `http://192.168.0.77:8096/` | `8096` | ✅ Ativo | Streaming de mídia (Interface de Admin). |
| **103** | MySpeed | LXC | `http://192.168.0.192:5216/` | `5216` | ✅ Ativo | Monitoramento de velocidade. |
| **104** | QbitTorrent | LXC | `http://192.168.0.96:8090/` | `8090` | ✅ Ativo | Cliente Torrent. **Possui VPN (NordVPN) configurada.** |
| **112** | Grafana | LXC | `http://192.168.0.228:3000` | `3000` | ✅ Ativo | Visualização de métricas e dashboards. |
| **113** | InfluxDB | LXC | `http://192.168.0.81:8086/` | `8086` | ✅ Ativo | Banco de dados de séries temporais. |
| **114** | Nginx Proxy Manager | LXC | `http://192.168.0.64:81/` | `81` | ⏸️ Desativado | Reverse proxy & SSL. **Conflita com NordVPN do navegador.** |

**Nota:** Apenas serviços ativos listados (exceto 114, mantido para referência). Credenciais em `CREDENTIALS.md`.


---

## 5. Gerenciamento e Compartilhamento de Armazenamento

Esta seção detalha como o HDD externo de 12TB é acessado pelos serviços virtuais.

### 5.1 Estrutura de Armazenamento no Host

* **Ponto de Montagem do HDD:** `/mnt/externalhdd`
* **Estrutura Padrão:** `/mnt/externalhdd/<pastas>`

---

## 6. Próximos Passos (Ações Pendentes)

Esta seção lista os itens que precisam ser confirmados e documentados para completar o projeto.

### 6.1 Ações de Documentação Pendentes

1.  **Documentar Backups:** Definir e detalhar a política de backup (destino, frequência, retenção) para VMs e LXCs críticos.

### 6.2 Estratégia de Backup (A Ser Detalhada)

* **VMs/LXC:** Usar a funcionalidade `vzdump` do Proxmox para backup agendado.
* **Destino de Backup:** [Definir o destino do backup: `local` ou outro disco de backup].
* **Backup Offsite (3-2-1):** [Definir se a nuvem será usada para cópias offsite de dados críticos (ex: configs do HomeAssistant)].

---

## 7. DNS e Configurações de Rede Detalhadas

### 7.1 Configuração DNS
| Tipo | Servidor | Porta | Observações |
| :--- | :--- | :--- | :--- |
| **DNS Primário** | AdGuard (`192.168.0.52`) | 53 | Bloqueio de anúncios e filtragem |
| **DNS Fallback** | Cloudflare (`1.1.1.1`) | 53 | Backup quando AdGuard falha |

### 7.2 Configuração de Rede
* **Máscara de Sub-rede:** `/24` (Padrão, 255.255.255.0)
* **Range de IPs:** `192.168.0.1` - `192.168.0.254`]

---

## 8. Monitoramento

### 8.1 Recursos do Sistema
| Métrica | Ferramenta | Dashboard |
|---------|------------|-----------|
| Recursos do Host | Proxmox Built-in | `192.168.0.88:8006` |
| Temperatura CPU | Grafana/Prometheus | [A ser configurado] |
| Uso de Rede | Grafana/Prometheus | [A ser configurado] |

---

## 9. Comandos e Ferramentas Úteis

### 9.1 Monitoramento de Disco
```bash
# Verificar saúde do disco
smartctl -a /dev/sda

# Monitorar I/O em tempo real
iotop
iostat -x 1

# Verificar uso do disco
df -h
du -sh /*
```

### 9.2 Monitoramento de Sistema
```bash
# Monitoramento de recursos
htop
free -h
vmstat 1

# Monitoramento de rede
iftop
netstat -tulpn
```

### 9.3 Comandos LXC/Proxmox
```bash
# Listar containers
pct list

# Status de um container específico
pct status CONTAINER_ID

# Entrar em um container
pct enter CONTAINER_ID

# Reiniciar container
pct restart CONTAINER_ID
```

---

## 10. Procedimentos de Manutenção

### 10.1 Atualização de Sistema
```bash
# Atualização do Proxmox Host
apt update && apt upgrade -y

# Atualização dos Containers
pct list # Listar containers
pct enter CONTAINER_ID
apt update && apt upgrade -y
```

### 10.2 Backup e Restore
```bash
# Backup de container
vzdump CONTAINER_ID --compress zstd

# Restore de backup
pct restore CONTAINER_ID /var/lib/vz/dump/vzdump-lxc-CONTAINER_ID.tar
```

---

## 11. Troubleshooting

| Problema | Verificação | Solução |
|----------|------------|----------|
| Container não inicia | `pct status CONTAINER_ID` | Verificar logs: `pct enter CONTAINER_ID` |
| Disco cheio | `df -h` | Limpar `/var/log/` e backups antigos |
| DNS não responde | `ping 192.168.0.52` | Reiniciar container do AdGuard |
| Alto uso de CPU | `htop` | Verificar processos e limitar recursos do container |
| qBittorrent: Trocar servidor NordVPN | `systemctl status openvpn-client@nordvpn` | Ver [Seção 11.1](#111-nordvpn-no-lxc-qbittorrent---trocar-de-servidor) |

### 11.1 NordVPN no LXC qBittorrent - Trocar de Servidor

**Problema:** Necessidade de trocar de servidor VPN do NordVPN no LXC qBittorrent.

**Solução Passo a Passo:**

1. **Parar o serviço OpenVPN:**
   ```bash
   systemctl stop openvpn-client@nordvpn
   ```

2. **Selecionar novo arquivo de configuração:**
   - Os arquivos de configuração estão em: `/etc/openvpn/client/ovpn_udp/`
   - Exemplo de arquivo disponível: `br75.nordvpn.com.udp.ovpn`

3. **Copiar arquivo para configuração padrão:**
   ```bash
   cp /etc/openvpn/client/ovpn_udp/br75.nordvpn.com.udp.ovpn /etc/openvpn/client/nordvpn.conf
   ```

4. **⚠️ Atualizar credenciais no arquivo copiado:**
   - Editar o arquivo `/etc/openvpn/client/nordvpn.conf`
   - Na **linha 22**, localizar: `auth-user-pass`
   - Substituir por: `auth-user-pass /etc/openvpn/credentials/nordvpn.txt`
   - Este arquivo contém as credenciais de login do NordVPN
   
   ```bash
   # Exemplo de edição com sed
   sed -i 's/^auth-user-pass$/auth-user-pass \/etc\/openvpn\/credentials\/nordvpn.txt/' /etc/openvpn/client/nordvpn.conf
   ```

5. **Reiniciar o serviço OpenVPN:**
   ```bash
   systemctl start openvpn-client@nordvpn
   ```

**Alternativa:** Rebootar o LXC (o OpenVPN está configurado para iniciar automaticamente ao boot):
   ```bash
   reboot
   ```

**Verificação:** Confirmar que a VPN está conectada:
   ```bash
   # Verificar status
   systemctl status openvpn-client@nordvpn
   
   # Verificar IP da VPN (deve ser diferente do IP original)
   curl ifconfig.me
   ```

---

## 12. Segurança e Boas Práticas

### 12.1  Gerenciamento de Credenciais

> **Arquivo separado:** Todas as credenciais estão em \CREDENTIALS.md\
> -  **Em \.gitignore\** - Protegido de exposição acidental no GitHub
> -  **Apenas local** - Nunca será versionado
> -  **Bem documentado** - Organize por serviço

**Nunca adicione credenciais ao README.md!**

### 12.2 Hardening do Proxmox

1. **Firewall do Proxmox**
   \\\ash
   # Habilitar firewall
   pve-firewall enable
   
   # Restringir acesso à WebUI
   # Editar: /etc/pve/firewall/nodes/NODENAME/host.fw
   \\\

2. **Atualização Automática**
   \\\ash
   # Configurar atualizações automáticas de segurança
   apt install unattended-upgrades
   \\\

3. **SSH Hardening**
   \\\ash
   # Editar /etc/ssh/sshd_config
   PermitRootLogin no
   PasswordAuthentication no
   PubkeyAuthentication yes
   Port 22 # Alterar para porta customizada
   \\\

### 12.3 Network Segmentation (Futuro)

- [ ] Implementar VLANs para serviços críticos (HomeAssistant, InfluxDB)
- [ ] Segmentar tráfego de mídia (Jellyfin) em VLAN separada
- [ ] Configurar firewall de aplicação (WAF) para serviços expostos
- [ ] Isolar containers de risco (qBitTorrent com VPN)

### 12.4 Monitoramento de Segurança

- [ ] Ativar logs de auditoria do Proxmox
- [ ] Monitorar tentativas de login falhadas
- [ ] Alertas automáticos em Grafana para uso anormal de recursos
- [ ] Manter registro de mudanças em \/etc/\ via \etckeeper\
- [ ] Verificar regularmente logs de acesso HTTP/HTTPS

### 12.5 Backup Seguro

- [ ] Implementar backup criptografado offsite (3-2-1 rule)
- [ ] Testar restore regularmente (pelo menos 1x por mês)
- [ ] Manter chaves de criptografia em local seguro e separado
- [ ] Manter versões anteriores de backups para recuperação de ransomware
- [ ] Fazer backup do arquivo \CREDENTIALS.md\ de forma segura

### 12.6 Checklist de Segurança Inicial

- [ ] Alterar todas as senhas padrão de admin (especialmente Jellyfin, qBitTorrent, Grafana)
- [ ] Habilitar HTTPS com certificado válido (Let's Encrypt)
- [ ] Configurar 2FA nos containers críticos
- [ ] Revisar e limitar permissões de disco para containers
- [ ] Desabilitar serviços não utilizados nos containers
- [ ] Manter registro de todas as mudanças

---

##  Referências Rápidas
| Recurso | Link | Descrição |
|---------|------|-----------|
| **Credenciais** | \CREDENTIALS.md\ | Senhas, tokens e chaves (não no git) |
| **Proxmox Web** | \https://192.168.0.88:8006\ | Interface de gerenciamento |
| **HomeAssistant** | \http://homeassistant.local:8123\ | Automação residencial |
| **Grafana** | \http://192.168.0.228:3000\ | Dashboards de monitoramento |

---

**Última atualização:** Novembro 2025  
**Manutenedor:** mfrafael  
**Branch:** main  
** Credenciais:** Em \CREDENTIALS.md\ (local apenas)

