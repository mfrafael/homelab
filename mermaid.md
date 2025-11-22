---
config:
  layout: dagre
  theme: neo-dark
  look: neo
---
flowchart RL
 subgraph VMs["Virtual Machines"]
        HA["HomeAssistant<br>homeassistant.local:8123"]
  end
 subgraph LXCs["LXCs"]
        AdGuard["AdGuard DNS<br>192.168.0.52"]
        Grafana["Grafana<br>192.168.0.228:3000"]
        InFluxDB["InFluxDB<br>192.168.0.81:8086"]
        MySpeed["MySpeed<br>192.168.0.192:5216"]
        Jellyfin["Jellyfin<br>192.168.0.77:8096"]
        qBitTorrent["qBitTorrent<br>192.168.0.96:8090"]
  end
 subgraph Proxmox["Proxmox @ Beelink S13 Mini"]
        VMs
        LXCs
  end
    Modem["Modem ISP<br>192.168.1.1"] <==> Router["Router Archer AX12<br>GW: 192.168.0.1"]
    Router === Proxmox
    Router <-. DNS Query .-> AdGuard
    HDD["HDD Externo<br>24TB Exos"] == "USB 3.0" === Proxmox
    HDD -. Mount: /mnt/externalhdd .-> Jellyfin & qBitTorrent

    HA@{ shape: card}
    Modem@{ shape: dbl-circ}
    HDD@{ shape: disk}
     HA:::vm
     AdGuard:::lxc
     Grafana:::lxc
     InFluxDB:::lxc
     MySpeed:::lxc
     Jellyfin:::lxc
     qBitTorrent:::lxc
     Modem:::hardware
     Router:::hardware
     HDD:::storage