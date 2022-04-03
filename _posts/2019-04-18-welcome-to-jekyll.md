---
title: "Welcome to AIS !"
date: 2022-04-18T15:34:30-04:00
categories:
  - AIS
tags:
  - AIS
  - Réseau
  - DHCP
  - Windows server
---

## REste à voir :
- comment gérer les images

```ruby
def print_hi(name)
  puts "Hi, #{name}"
end
print_hi('Tom')
#=> prints 'Hi, Tom' to STDOUT.
```

Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/

configuration du serveur DHCP sur la VM

Je spécifie une ip fixe 169.254.12.10 puis je vais paramétrer mon serveur DHCP en cliquant sur choisir un rôle

J’ai sélectionné DHCP, `entrer`

<img src=":/1a7c6d5db9f742ddb5786997e8a2084b" alt="20a1c228fe1555792d233663aee3a64f.png" width="547" height="414" class="jop-noMdConv">

Je laisse toutes les options à blanc  `entrer`

<img src=":/f60d0b31595e4b31bd196696b373085c" alt="c96f35c301a168ade93cda7654283856.png" width="544" height="399" class="jop-noMdConv">

pas de wins `entrer`

<img src=":/9601ef4a7042495f8eb4d945526e7eba" alt="793100713bc7b296364c4b1470879e41.png" width="569" height="394" class="jop-noMdConv">

Comme je n’avais pas encore fait les calculs je n’ai pas défini de plage d’adresses. Je reviens donc plus tard dessus via le Gestionnaire de serveur clic droit et on peut ajouter des services, options, redémarrer …)

`ipconfig /release`

`ipconfig /renew`

Le pc prend bien une adresse ip incluse dans la plage définie sur le serveur DHCP

`ipconfig /all`
