# Images extraites des fiches PDF

Dix photographies JPEG sont extraites directement des PDF livrés : cinq dans `fours/`, cinq dans `serveurs/`. Les PDF restent dans `documents/` et sont inchangés. Chaque fichier `.jpg` porte le même nom de base que son PDF parent.

Ces JPEG sont les images effectivement incorporées aux PDF, déjà adaptées à la fiche (taille et compression ; recadrage de fours_photo_01). Ils ne sont pas présentés comme les originaux plein format téléchargés. L’extraction ne réencode pas les images. Les URL des originaux, auteurs et licences sont conservés dans les registres.

Les 40 lignes de `../inventaire.csv` correspondent aux 40 documents PDF. Les dix images sont des ressources associées, reliées dans la colonne remarques et dans les registres ci-dessous ; elles ne portent pas le nombre de documents à 50.

| Image | PDF parent | Page | Licence |
|---|---|---:|---|
| [fours_photo_01.jpg](fours/fours_photo_01.jpg) | [fours_photo_01.pdf](../documents/fours/fours_photo_01.pdf) | 1 | [CC BY-SA 3.0 PL](https://creativecommons.org/licenses/by-sa/3.0/pl/) |
| [fours_photo_02.jpg](fours/fours_photo_02.jpg) | [fours_photo_02.pdf](../documents/fours/fours_photo_02.pdf) | 1 | [CC BY-SA 3.0 PL](https://creativecommons.org/licenses/by-sa/3.0/pl/) |
| [fours_photo_03.jpg](fours/fours_photo_03.jpg) | [fours_photo_03.pdf](../documents/fours/fours_photo_03.pdf) | 1 | [CC BY-SA 3.0 PL](https://creativecommons.org/licenses/by-sa/3.0/pl/) |
| [fours_photo_04.jpg](fours/fours_photo_04.jpg) | [fours_photo_04.pdf](../documents/fours/fours_photo_04.pdf) | 1 | [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) |
| [fours_photo_05.jpg](fours/fours_photo_05.jpg) | [fours_photo_05.pdf](../documents/fours/fours_photo_05.pdf) | 1 | [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) |
| [serveurs_photo_06.jpg](serveurs/serveurs_photo_06.jpg) | [serveurs_photo_06.pdf](../documents/serveurs/serveurs_photo_06.pdf) | 1 | [CC BY-SA 2.0](https://creativecommons.org/licenses/by-sa/2.0/) |
| [serveurs_photo_07.jpg](serveurs/serveurs_photo_07.jpg) | [serveurs_photo_07.pdf](../documents/serveurs/serveurs_photo_07.pdf) | 1 | [CC BY-SA 2.0](https://creativecommons.org/licenses/by-sa/2.0/) |
| [serveurs_photo_08.jpg](serveurs/serveurs_photo_08.jpg) | [serveurs_photo_08.pdf](../documents/serveurs/serveurs_photo_08.pdf) | 1 | [CC BY-SA 2.0](https://creativecommons.org/licenses/by-sa/2.0/) |
| [serveurs_photo_09.jpg](serveurs/serveurs_photo_09.jpg) | [serveurs_photo_09.pdf](../documents/serveurs/serveurs_photo_09.pdf) | 1 | [CC BY-SA 2.0](https://creativecommons.org/licenses/by-sa/2.0/) |
| [serveurs_photo_10.jpg](serveurs/serveurs_photo_10.jpg) | [serveurs_photo_10.pdf](../documents/serveurs/serveurs_photo_10.pdf) | 1 | [domaine public - déclaration de l’auteur](https://commons.wikimedia.org/wiki/File:Dell_PowerEdge_Servers.jpg) |

`tracabilite_images.csv` et `.json` indiquent la page, l’objet image du PDF, les dimensions, les empreintes SHA-256 du JPEG et du PDF parent, la source originale, l’auteur, les droits et les transformations. Pour vérifier : ouvrir le JPEG et le PDF indiqué, ou comparer le JPEG au flux image extrait de la page.
