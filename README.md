# A propos

Ce dépôt est une bouée de sauvetage en cas de formatage et me permet de noter les choses à savoir concernant mon installation de Linux.

[![Aperçu](screenshot.png)](https://raw.githubusercontent.com/Grafikart/dotfiles/master/screenshot.png)

La liste des paquets installés sur ma machine sont disponibles dans le fichier package.list. Les paquets AUR sont en fin de liste

```
cat package.list | xargs yaourt -S --needed --noconfirm
```

# Trucs & Astuces

## DuckDuckGo

Le thème duckduckgo 

- [Nord Theme](https://duckduckgo.com/?kae=d&k7=222D32&kj=1d272b&ko=d&kaa=B48EAD&k9=5E81AC&ku=-1&k8=828e9a&kx=A3BE8C&kai=1&k18=-1&kw=n&kg=g&kz=1&kc=-1&kac=-1&kaj=m&kam=bing-maps&kak=-1&kax=-1&kaq=-1&kap=-1&kao=-1)

## firefox Colors

https://color.firefox.com/?theme=XQAAAAIUAQAAAAAAAABBqYhm849SCia2CaaEGccwS-xNKlhX7p_w-bFKDpbUJasOFEb7xDbBpLNSPVGezz8UbhQdB0GWAOD8ATi6goq1YnVG0pMl-SnqDQaOZUOSxI6hRIBBN9cVab3KfaEVnFT8UNixHiWH8LmtKyl93ZVGkBz-kvmbxdqRTnOGOGFU-foQOhnFUiStVUkW2aOPtoZpBAT0yl-BvxEp9675M_ZheGwrw9AtoVcGBsMl1TfdZDrqm1YIX837L_-cMyoA

## Tearing Nvidia

Le pilote propriétaire nvidia rajoute un tearing atroce :

- Utiliser nvidia settings pour gérer les settings
- Exporter la configuration et ajouter  `{ ForceCompositionPipeline = On }` dans la partie metamodes de "Screen"

## Remapper les boutons de la souris

[![EasyStroke permet  de remapper les boutons de la souris](screenshots/easystroke.png)](https://raw.githubusercontent.com/Grafikart/dotfiles/master/screenshots/easystroke.png)

## Remapper touches du clavier

Pour remplacer une touche par une autre. Je l'utilise pour remplacer la touche puissance 2 par un back-tick.

```
# On génère le fichier de map
xmodmap -pke > ~/.Xmodmap
# On trouve la clef a remap
xev | awk -F'[ )]+' '/^KeyPress/ { a[NR+2] } NR in a { printf "%-3s %s\n", $5, $8 }'
# On modifie le fichier Xmodmap et on teste avec
xmodmap ~/.Xmodmap
```

## Trouver le process qui utilise un port

```
sudo netstat -nlp | grep :80
```
