---
title: "Splash Page : Config DHCP sur Windows Server 2008"
layout: splash
permalink: /splash-page/
date: 2022-04-08
header:
  overlay_color: #"#000"
  overlay_filter: #"0.5"
  overlay_image: ![unsplash-image-9](https://user-images.githubusercontent.com/87373259/162613253-94a97ad1-3fe2-46ba-bb47-0f0c380c2aac.jpg)
  caption: "Photo credit: [**Unsplash**](https://unsplash.com)"
  actions:
    - label: "Download"
      url: "https://github.com/mmistakes/minimal-mistakes/"
excerpt: "Texte sur l'image, aligné à gauche."
intro: 
  - excerpt: 'texte d'intro sous le header *proin faucibus*, markdown ok, centré. Centered with `type="center"`'
---

{% include feature_row id="intro" type="center" %}


-------------------------------------
  
  ![styled-image](https://user-images.githubusercontent.com/87373259/161559675-ddee4a87-d1e7-4fdb-bb7f-fb1f0819ca09.jpg "Blondin"){: .align-center style="width: 50%;"} __Photo de Blondin à 50%, centrée__{: style="text-align: center;"}



Configuration du serveur DHCP sur la VM

Je spécifie une ip fixe 169.254.12.10 puis je vais paramétrer mon serveur DHCP en cliquant sur choisir un rôle

J’ai sélectionné DHCP, `entrer`
html
<img src="https://hullaballo2001.github.io/OR_Notes/assets/images/20a1c228fe1555792d233663aee3a64f.png" alt="20a1c228fe1555792d233663aee3a64f.png" width="547" height="414" class="jop-noMdConv">




Je laisse toutes les options à blanc  `entrer`

<img src="https://hullaballo2001.github.io/OR_Notes/assets/images/c96f35c301a168ade93cda7654283856.png" alt="c96f35c301a168ade93cda7654283856.png" width="544" height="399" class="jop-noMdConv">

pas de wins `entrer`


> Comme je n’avais pas encore fait les calculs je n’ai pas défini de plage d’adresses. Je reviens donc plus tard dessus via le Gestionnaire de serveur clic droit et on peut ajouter des services, options, redémarrer …)

*italique*

**gras**

![blondin](https://user-images.githubusercontent.com/87373259/161559675-ddee4a87-d1e7-4fdb-bb7f-fb1f0819ca09.jpg)

