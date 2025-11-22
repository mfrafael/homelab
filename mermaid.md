---
config:
  layout: dagre
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
    Modem["Modem ISP<br>192.168.1.1"] ==> Router["Roteador Principal<br>GW: 192.168.0.1"]
    Router ==> Proxmox
    Router -. DNS Query .-> AdGuard
    HDD["HDD Externo<br>24TB Exos"] == "USB 3.0" === Proxmox
    HDD -. Mount: /mnt/externalhdd .-> Jellyfin & qBitTorrent

    HA@{ shape: card}
    HDD@{ shape: cyl}
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
    classDef internet fill:#30323a,stroke:#8f63ff,stroke-width:2px,color:#e2e2e2
    classDef hardware fill:#30323a,stroke:#69a7ff,stroke-width:2px,color:#e2e2e2
    classDef storage fill:#1f1f23,stroke:#b47f37,stroke-width:2px,color:#e7d7b7
    classDef vm fill:#4a2e2e,stroke:#ff7043,stroke-width:2px,color:#ffd5c2
    classDef lxc fill:#1f2f3a,stroke:#4fc3f7,stroke-width:2px,color:#d8f3ff
    style Modem fill:#272a30,stroke:#7a7f87,stroke-width:2px,color:#e2e2e2
    style Router fill:#272a30,stroke:#7a7f87,stroke-width:2px,color:#e2e2e2
    style Proxmox fill:#3a3d45,stroke:#ffb347,stroke-width:2px,color:#ffe8c6