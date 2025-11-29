# 🏠 HOMELAB NOTES - Quick Reference

## 📌 Hardware Base
- **Servidor:** Beelink S13 (Intel N150, 16GB RAM, 512GB SSD)
- **Proxmox:** Debian 13 "Trixie"
- **IP Management:** `192.168.0.88:8006`
- **HDD Externo:** 24TB Seagate Exos (Enterprise-grade, 7200 RPM)
  - Mount: `/mnt/externalhdd`
  - Device: `/dev/sda`
  - WWN: `5000c500e8a3a9ac`

---

## 🌐 Rede
| Função | IP | Observações |
|--------|----|----|
| Gateway | `192.168.0.1` | Roteador principal |
| Proxmox Host | `192.168.0.88` | Hypervisor |
| DNS Primário | `192.168.0.52` | AdGuard (bloqueio de anúncios) |
| DNS Fallback | `1.1.1.1` | Cloudflare |
| **Range LAN** | `192.168.0.1 - 192.168.0.254` | /24 (255.255.255.0) |

---

## 🖥️ Serviços Ativos (7)

| ID | Serviço | IP | Porta | Tipo | Status |
|----|---------|----|----|------|--------|
| 100 | HomeAssistant | homeassistant.local | 8123 | VM | ✅ |
| 101 | AdGuard | 192.168.0.52 | 53/80 | LXC | ✅ |
| 102 | Jellyfin | 192.168.0.77 | 8096 | LXC | ✅ |
| 103 | MySpeed | 192.168.0.192 | 5216 | LXC | ✅ |
| 104 | QbitTorrent | 192.168.0.96 | 8090 | LXC | ✅ (⚠️ VPN NordVPN) |
| 112 | Grafana | 192.168.0.228 | 3000 | LXC | ✅ |
| 113 | InfluxDB | 192.168.0.81 | 8086 | LXC | ✅ |
| 114 | Nginx Proxy Mgr | 192.168.0.64 | 81 | LXC | ⏸️ (conflita VPN) |

---

## 💾 Armazenamento
```
/mnt/externalhdd/
├── Media/
│   ├── Movies/
│   └── TV Shows/
```
---

## ⚙️ Comandos Essenciais

### LXC/VM Management
```bash
pct list                    # Listar todos LXCs
pct status <ID>             # Status de um LXC
pct enter <ID>              # Entrar no console
pct restart <ID>            # Reiniciar
pct start <ID>              # Iniciar
pct stop <ID>               # Parar
```

### Monitoramento de Disco
```bash
smartctl -a /dev/sda        # SMART Status
df -h                       # Espaço em disco
du -sh /mnt/externalhdd/*   # Uso por pasta
iotop                       # I/O em tempo real
```

### Sistema
```bash
htop                        # Monitor de recursos
free -h                     # Memória disponível
uptime                      # Tempo de funcionamento
```

---

## 🔧 Backup via Proxmox

```bash
# Backup de container/VM
vzdump <CONTAINER_ID> --compress zstd

# Restore de backup
pct restore <CONTAINER_ID> /var/lib/vz/dump/vzdump-lxc-*.tar

# Listar backups
ls -lah /var/lib/vz/dump/
```

---

## 🚨 Troubleshooting Rápido

| Problema | Comando |
|----------|---------|
| Container não inicia | `pct status <ID>` + `pct enter <ID>` |
| DNS não responde | `ping 192.168.0.52` → Reiniciar AdGuard |
| Alto uso CPU | `htop` → Verificar container |
| Disco cheio | `df -h` → Limpar `/var/log/` |
| Conexão SSH lenta | Verificar QbitTorrent (VPN) |
| Confirmar IP | `curl ifconfig.me` |
| **QBit: Trocar servidor NordVPN** | 
```bash
systemctl stop openvpn-client@nordvpn
curl ifconfig.me
cp /etc/openvpn/client/ovpn_udp/br75.nordvpn.com.udp.ovpn /etc/openvpn/client/nordvpn.conf
sed -i 's/^auth-user-pass$/auth-user-pass \/etc\/openvpn\/credentials\/nordvpn.txt/' /etc/openvpn/client/nordvpn.conf
systemctl start openvpn-client@nordvpn
curl ifconfig.me
```
|


---

## 🔐 Segurança

**⚠️ CREDENCIAIS:** Arquivo separado `CREDENTIALS.md` (local, não no git)

### Hardening Checklist
- [ ] SSH: PermitRootLogin no
- [ ] SSH: PasswordAuthentication no (usar chaves)
- [ ] Proxmox Firewall: Habilitado
- [ ] HTTPS: Certificados válidos
- [ ] 2FA: Ativado nos serviços críticos
- [ ] Backups: Testados 1x/mês

---

## 📊 Monitoramento

| Ferramenta | Acesso | Dashboard |
|------------|--------|-----------|
| Proxmox | `192.168.0.88:8006` | Recursos do host |
| Grafana | `192.168.0.228:3000` | Métricas & gráficos |
| InfluxDB | `192.168.0.81:8086` | Time-series DB |

---

## 📋 Checklist de Manutenção Mensal

- [ ] Verificar SMART do HDD externo
- [ ] Revisar uso de disco
- [ ] Verificar logs de erro em containers
- [ ] Testar restore de backup
- [ ] Atualizar Proxmox + Containers
- [ ] Revisar espaço em `/var/log/`
- [ ] Validar heartbeat dos serviços críticos

---

## 🔗 Links Rápidos

- **Proxmox WebUI:** https://192.168.0.88:8006
- **Grafana:** http://192.168.0.228:3000
- **HomeAssistant:** http://homeassistant.local:8123
- **Jellyfin:** http://192.168.0.77:8096
- **AdGuard:** http://192.168.0.52

---

**Última atualização:** Novembro 2025  
**Proxmox Node:** Beelink S13  
**Backup Status:** ✅ Ativo  
**InfluxDB Status:** ✅ Ativo

---


## 📊 Diagrama de Conexões

<img src="/pve2/images/diagram.svg" alt="Diagrama da Arquitetura do Homelab">