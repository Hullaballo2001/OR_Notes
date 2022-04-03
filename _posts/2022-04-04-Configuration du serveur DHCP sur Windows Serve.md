configuration du serveur DHCP sur la VM

Je spécifie une ip fixe 169.254.12.10 puis je vais paramétrer mon serveur DHCP en cliquant sur choisir un rôle

J’ai sélectionné DHCP, `entrer`

<img src="../../../_resources/20a1c228fe1555792d233663aee3a64f.png" alt="20a1c228fe1555792d233663aee3a64f.png" width="547" height="414" class="jop-noMdConv">

Je laisse toutes les options à blanc  `entrer`

<img src="../../../_resources/c96f35c301a168ade93cda7654283856.png" alt="c96f35c301a168ade93cda7654283856.png" width="544" height="399" class="jop-noMdConv">

pas de wins `entrer`


Comme je n’avais pas encore fait les calculs je n’ai pas défini de plage d’adresses. Je reviens donc plus tard dessus via le Gestionnaire de serveur clic droit et on peut ajouter des services, options, redémarrer …)

<img src="../../../_resources/094e47e4fb649d78733e57b952e91fe3.png" alt="094e47e4fb649d78733e57b952e91fe3.png" width="286" height="307" class="jop-noMdConv">

<img src="../../../_resources/131b00bc2dd82be3c5a9eabeac44f531.png" alt="131b00bc2dd82be3c5a9eabeac44f531.png" width="539" height="258" class="jop-noMdConv"> 

 <img src="../../../_resources/9716a377de18e8bbdbec8dbeaa0ab649.png" alt="9716a377de18e8bbdbec8dbeaa0ab649.png" width="329" height="279" class="jop-noMdConv">

Enfin, connexion du pc client après avoir changé son mode d’acquisition d’adresse ip en automatique

<img src="../../../_resources/251af7f02447b2dc917affbf46be8ed1.png" alt="251af7f02447b2dc917affbf46be8ed1.png" width="289" height="300" class="jop-noMdConv">

`ipconfig /release`

`ipconfig /renew`

Le pc prend bien une adresse ip incluse dans la plage définie sur le serveur DHCP

`ipconfig /all`

<img src="../../../_resources/11bccebb4a6a1e3fa89c669e0b3d2cf2.png" alt="11bccebb4a6a1e3fa89c669e0b3d2cf2.png" width="490" height="397">
