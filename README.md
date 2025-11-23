# Automatisation Aruba CX – NAC, MLAG et Routage BGP

Ce projet a pour objectif d'automatiser la configuration d'une infrastructure réseau basée sur des switches **Aruba CX**.  
Il couvre les aspects suivants :

- **Intégration NAC** (MAB)
- **Configuration MLAG** (VSX entre deux switches Aruba CX)
- **Routage BGP et OSPF** 
- **Configuration des interfaces** (Access, Trunk, Uplink, Management)


---

## L’infrastructure typique est composée de :

- **Un Switch Aruba CX Router**
- **Deux switches Aruba CX** en **VSX Pair** (MLAG) pour la distribution en VSX
- **Deux switch Aruba CX** pour l Acces
- Prototocole de routage BGP


## Les repositorie CX

CX-Network/ansible-projet-aruba-CX/
│
├── inventory/
│ └── production/

│  ├── group_vars/
│  │     ├── acces.yml
│  │     ├── all.yml
│  │     ├── distribution.yml
│  │     ├── vault.yml # Variables chiffrées (mots de passe, clés)
│  │     └── wan.yml

│  ├── host_vars/
│  │     ├── arubaCX-Rt1.yml
│  │     ├── arubaCX-SWA01.yml
│  │     ├── arubaCX-SWA02.yml
│  │     ├── arubaCX-SWD01.yml
│  │     └── arubaCX-SWD02.yml
│  └── hosts.yml

│
├── roles/
│ ├── access_switch/
│ │    ├── tasks/main.yml
│ │    └── templates/
│ │       ├── acces_ports.j2
│ │       ├── base_system.j2
│ │       ├── portchannel_l2_uplink.j2
│ │       ├── security.j2
│ │       ├── static_ports.j2
│ │       └── vlans.j2

│ │
│ ├── distribution_vsx/
│ │     ├── tasks/main.yml
│ │     └── templates/
│ │         ├── acls.j2
│ │         ├── base_system.j2
│ │         ├── bgp.j2
│ │         ├── ospf.j2
│ │         ├── port_lags_bgp_wan.j2
│ │         ├── port_lags_l2_access.j2
│ │         ├── prefix-lists.j2
│ │         ├── route-maps.j2
│ │         ├── vlans.j2
│ │         ├── vsx.j2
│ │         └── vsx_id.j2

│ │
│ └── wan_router/
│     ├── tasks/main.yml
│     └── templates/
│        ├── acls.j2
│        ├── base_system.j2
│        ├── bgp.j2
│        ├── port_lags_bgp_distribution.j2
│        ├── prefix-lists.j2
│        ├── route-maps.j2
│        ├── vlans.j2
│        └── wan_interfaces.j2

│
├── playbook-deploy-access.yml
├── playbook-deploy-distribution.yml
├── playbook-deploy-wan.yml
├── requirements.yml
└── README.md
