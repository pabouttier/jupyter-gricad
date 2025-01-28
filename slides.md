---
marp: true
theme: socrates
author: Pierre-Antoine Bouttier
paginate: true
transition: vertical-scroll 0.25s
footer: pierre-antoine.bouttier@univ-grenoble-alpes.fr - CC BY-SA 4.0
---

<!-- _transition: cover 0.25s -->

<!-- _class: titlepage -->

![bg left:33%](./fig/jupycad.png)

# Jupyter@GRICAD
## Réflexions sur la fourniture d'interface de type notebooks aux infras GRICAD

### P-A Bouttier, 28/01/2025

---

<!-- _transition: none -->

# TOC

<!-- _class: cool-list -->

1. *Contexte*
3. *Pistes imaginées*

---
# TOC

<!-- _class: cool-list -->

1. ***Contexte***
3. *Pistes imaginées*

---
# Nouveaux usages

- Nouvelles communautés : moins de compétences devlog ou juste linux/cli
- IA
- Notebooks comme outils de travail collaboratifs, notamment en analyse/traitement de données (et pré- et post-traitement)
- Diffusion de la production (articles et code/tutos/HOWTO)
- Formations (dans le cadre MesoNET)

---
# Solutions actuelles à GRICAD

- JupyterHub, & BinderHub
- Jupyter(Lab|Hub) lancé sur les noeuds de calcul HPC
- (Jupyterlite)

---
# Y répond-on ? (1/2)

- Aspect collaboratif (au sein d'une équipe, d'un projet, données communes, espaces cloisonnés) : 
  - JupyterHub & BinderHub **Non** 
  - JupyterHPC : **oui au niveau des données, à plusieurs sur un même job ?**
- Passage à l'échelle : 
  - JupyterHub & BinderHub : **difficile/ça dépend**
  - JupyterHPC : Oui, mais consommation de ressources. Mode interactif. 

---
# Y répond-on (2/2)

- Pré- et post-traitement
  - JupyterHub & BinderHub : **Non**
  - JupyerHPC : **oui, en interactif**
- Formations : 
  - JupyterHub & BinderHub : **oui, mais dans un cadre standard**
  - JupyterHPC : **oui mais avec des interventions adhoc côté perseus**

- Facilité d'accès : 
  - JupyterHub & BinderHub : **oui dans le cadre agalan/UGA**
  - JupyterHPC : **oui** pour l'authentif de façon large (perseus), **non** dans l'aspect technique

<!-- _transition: cover 0.25s -->

---
# TOC

<!-- _class: cool-list -->

1. *Contexte*
3. ***Pistes imaginées***

---
# JupyterHPC 

Sur un pool de ressources dédiées (mais ajustable : e.g. noeuds devel), permet aux utilisateurs : 
- De se connecter à une interface web via id perseus
- sur laquelle il sélectionne un gabarit de ressources
- Qui spawne un jupyterLab sur ses ressources 
- Et le connecte automatiquement dessus

---
# Compléments

- Mode interactif donc limitation de la surface de ressources réservables(cpu/gpu, walltime)
- Le notebook entier tourne sur le noeud (amha, plus simple à mettre en place) 
- Système semblable en place au CRIANN et bientôt dans certaines machines MesoNET. IDRIS c'est certaines cellules ? 

--- 
# Openstack & Jupyter as a Service 

Sur NOVA (partition MesoNET), plutôt que d'allouer des ressources :
- Déployer une instance JupyterHub/Lab (?)  
- Dans le périmètre d'un projet (authentif des collaborateurs)
- Pour un gabarit de ressources donné
- Pour un temps/créneau donné ? 
- Soit nu (et les users déposent leurs notebooks/data dessus) soit depuis un dépôt git contenant les données et les notebooks (et env log ?)


---

# Discussion

