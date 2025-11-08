# Automatisation Aruba CX – NAC, MLAG et Routage BGP

Ce projet a pour objectif d'automatiser la configuration d'une infrastructure réseau basée sur des switches **Aruba CX**.  
Il couvre les aspects suivants :

- **Intégration NAC** (ClearPass ou autre solution 802.1X)
- **Configuration MLAG** (VSX entre deux switches Aruba CX)
- **Routage BGP** (Underlay / Overlay / Peering)
- **Configuration des interfaces** (Access, Trunk, Uplink, Management)

---

## 

L’infrastructure typique est composée de :

- **Deux switches Aruba CX** en **VSX Pair** (MLAG)
- Un **ClearPass** ou solution NAC externe
- Un **routeur / Fabric / Core** pour le peering BGP

