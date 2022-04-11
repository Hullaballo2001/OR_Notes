---
title: "1.Build a GitHub Page static site"
updated: 2022-04-11 
created: 2022-04-07 
categories:
  - AIS
tags:
  - GH Pages
  - DIY
---

# Pour quoi faire ?

J’ai un dossier professionnel (DP) à monter pour pouvoir valider un titre RNCP d’Administrateur Infrastructures Sécurisées en juillet 2022. Je voudrais pouvoir regrouper, classer, mettre en valeur les markdowns (Joplin ❤️ ) des différents ateliers, quêtes, ctf … réalisés lors de ma formation d’Analyste Cybersécurité à la Wild Code School. Je ferai référence à ces travaux dans le DP, le site étant dans un premier temps une version très détaillée des différents ateliers.

# Start

Une fois le choix de GitHub pages fait, quelle est la suite. Je n’ai aucune compétence en développement web donc il me faut un truc tout fait. Mais comme j’aime bien bidouiller et que je voudrais pouvoir le faire évoluer pour ajouter des posts de blog, des articles techniques et regrouper les liens que je considère indispensables (système et réseau, hacking, CTI, géoplitique, … ).

Ce sera donc un site statique, avec un thème Jekyll “Jekyll is a static site generator with built-in support for GitHub Pages and a simplified build process. Jekyll takes Markdown and HTML files and creates a complete static website based on your choice of layouts. Jekyll supports Markdown and Liquid, a templating language that loads dynamic content on your site. For more information, see Jekyll.”

Je n’ai pas du tout envie, ni le temps de me plonger dans une installation en local et des git commit git push etc … Et ça tombe bien car il existe des dépôts tout faits, ready to go.

Je choisis Minimal Mistakes de Michael Rose : “Minimal Mistakes is a flexible two-column Jekyll theme. Perfect for hosting your personal site, blog, or portfolio on GitHub or self-hosting on your own server. As the name implies — styling is purposely minimalistic to be enhanced and customized by you 😄” “MM has been developed as a Gem-based theme for easier use, and 100% compatible with GitHub Pages when used as a **remote theme**.”

# Installation

Dans le repo de Minimal Mistake (MM), dans le ReadMe, dans la partie installation (pas trop dur ?) on voit un tentant “Looking for an example? Use the **Minimal Mistakes remote theme starter** for the quickest method of getting a GitHub Pages hosted site up and running. Generate a new repository from the starter, replace sample content with your own, and configure as needed.” –> https://github.com/mmistakes/mm-github-pages-starter/generate

OR_Notes est né le 4 mars 2022 👶

# Configuration/Customization, les trucs que je crois comprendre

Pour chaque fichier on peut le lire en cliquant dessus, l'éditer avec le crayon, le supprimer avec la poubelle, ...

<img src="../../_resources/2fb0918a4ef1ff8f251b2b554c3a6245.png" alt="2fb0918a4ef1ff8f251b2b554c3a6245.png" width="659" height="110">
![2fb0918a4ef1ff8f251b2b554c3a6245](https://user-images.githubusercontent.com/87373259/162174280-6d664490-4038-4ce4-a8d9-b14ab4519887.png)


Et quand on l'a modifié on ajoute un commentaire pour dire ce qu'on a fait "ajout de AIS 2022" par ex, et on "commit change". Cela (grâce à MM) lance directement la modification du code après vérification et la construction du site dans la foulée. Si problème la coche verte est remplacée par une croix rouge. Cliquer dessus pour essayer de comprendre ce qui ne lui a pas plut ...

Il y a possibilité de revenir en arrière en cliquant sur "History" en haut à droite puis "browse ... at this point"

![2c69d5b2457ef9c48e0bececfa1026fc.png](../../_resources/2c69d5b2457ef9c48e0bececfa1026fc.png)

## _data

### navigation.yml

Ca créé les boutons du haut de la page

```
main:
  - title: "AIS 2022"
    url: /ais2022/
  - title: "Posts"
    url: /posts/
  - title: "Categories"
    url: /categories/
  - title: "Tags"
    url: /tags/
  - title: "About"
    url: /about/
```

## _pages

Les pages par défaut et les options pratiques : tags, regroupement des posts par année et les catégories (déclarées dans le “cartouche” de chaque post)

![17befe571ba389e4989def96f11fc694.png](../../_resources/17befe571ba389e4989def96f11fc694.png)

Par ex la page  du 404 (noter les boutons du haut qui sont paramétrés dans le navigation.yml. Le pied de page (footer) et les boutons de gauche sont gérés dans le _config.yml

![f0c9bdd3e194e555db2519c59bdfe6e7.png](../../_resources/f0c9bdd3e194e555db2519c59bdfe6e7.png)

## _posts

Les articles de blog (posts) par défaut nous montrant les différentes possibilités de mise en forme, navigation ![5eb52289ad68c3cdab2813dbb53d6609.png](../../_resources/5eb52289ad68c3cdab2813dbb53d6609.png)

Comment ajouter un post ? “AddFile” en haut à droite et soit on en créé un vide qu’on peut écrire ex nihilo soit on importe un markdown. Pour ce faire il faut d’abord l’exporter en “Markdown + Front Matter” ce qui créé un dossier avec le .md et un autre dossier avec les ressources (images).

<img src="../../_resources/c1696f8ec0fb8ce227cddbe0b607a584.png" alt="c1696f8ec0fb8ce227cddbe0b607a584.png" width="421" height="219" class="jop-noMdConv">

Un ex de markdown modifié pour tester différentes choses :

Le “cartouche” c’est la partie Front Matter en haut entre les — ---

```
---
title: "Quête réseau 1 - Configuration d'un serveur DHCP sur Windows Server 2008"
categories:
  - AIS
tags:
  - AIS
  - DHCP
---

configuration du serveur DHCP sur la VM

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
```

## assets/images

Alors là c’est encore un peu obscur :

\- Soit on copie les images dans le dossier images avec “Add File” et on y fait référence avec les permalinks dans le texte en mettant une adresse complète  style ça en HTML

`<img src="https://hullaballo2001.github.io/OR_Notes/assets/images/c96f35c301a168ade93cda7654283856.png" alt="c96f35c301a168ade93cda7654283856.png" width="544" height="399" class="jop-noMdConv">`

\- Soit on peut, quand on est en édition d’un post aller en bas de l’éditeur et on clique sur "Attach files … " et cela nous insert, là où on est l’image choisie dans le dossier _ressources créé lors de l’export du markdown (ou sur le net, ou dans un autre dossier sur notre pc). Et là ça nous donne un tag kramdown de l'image.

![839e117da569c60c8b18420a0a0a989f.png](../../_resources/839e117da569c60c8b18420a0a0a989f.png)

Il y a une 3ème methode avec "liquid" mais je n'en suis pas encore là !

## _config.yml

C'est le coeur du site. On peut paramétrer ici les choses qu'on veut voir répéter sur plusieurs, voire toutes les pages du site. J'y vais option par option pour voir si les changements sont acceptés et si le résultat est bien tel qu'espéré !

Il mérite une page à lui tout seul (insert link)

# Questions

Il se passe tout un tas de trucs en bas de page ... aucune idée d'où tout cela est géré :frown: 

![8634ba784541e8c36c287d968eeb3be8.png](../../_resources/8634ba784541e8c36c287d968eeb3be8.png)

Comment créer un sommaire général (TOC), un plan du site (sitemap), et un sommaire pour chaque page ?


# Markdown dans MM

On a aussi kramdown[Permalink](https://www.fabriziomusacchio.com/blog/2021-08-11-Minimal_Mistakes_Cheat_Sheet/#kramdown "Permalink")The theme uses [*kramdown*](https://kramdown.gettalong.org/index.html), a library written in *Ruby*, that renders [*Markdown*](https://www.fabriziomusacchio.com/teaching/Markdown_Guide/) for [*Jekyll* websites](https://jekyllrb.com/docs/configuration/markdown/#kramdown). *kramdown* allows the usage of [block](https://kramdown.gettalong.org/quickref.html#block-attributes) and [inline](https://kramdown.gettalong.org/quickref.html#inline-attributes) attributes, which enables custom stylings to standard *Markdown* commands, e.g.,

# Autres sources de bonheur

GitHub Pages : https://pages.github.com/ https://docs.github.com/en/pages

Minimal Mistake : https://mmistakes.github.io/minimal-mistakes/about/ https://github.com/mmistakes/minimal-mistakes

Le site de jekyll : https://jekyllrb.com/

Jekyll pour GitHub (Front Matter) : https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/about-github-pages-and-jekyll

Pour la mise en forme de Jekyll dans MM (TOC, headers, encadrés, navigation, …) : [https://www.fabriziomusacchio.com/blog/2021-08-11-Minimal\_Mistakes\_Cheat_Sheet/](https://www.fabriziomusacchio.com/blog/2021-08-11-Minimal_Mistakes_Cheat_Sheet/)

Kramdown, mise en forme de markdown : https://kramdown.gettalong.org/quickref.html#inline-attributes
