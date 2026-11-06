# MAINTiDOC - corpus technique réel

Équipe : **BELOUANAS - Ayoub BELOUANAS**, EMSI. État au 6 novembre 2026.
Dépôt : https://github.com/ayoubbelouanas/maintidoc (branche codex/livraison-l1).

## Sources effectivement présentes

**33 PDF fabricants : 20 RATIONAL et 13 Dell**, aucun document synthétique actif. Les treize PDF Dell comprennent dix manuels propriétaires, deux guides techniques R720/R720xd et R730/R730xd, et un guide RAID PERC 9. Les guides iDRAC et Lifecycle Controller non ajoutés sont hors inventaire.

- RATIONAL : iCombi Pro, iCombi Classic, SelfCookingCenter, iHexagon ; configurations selon chaque notice.
- Dell : R220, R230, R320, R430, R520, R530, R620, R720, R720xd, R730, R730xd, T320 et T330 ; PERC 9 est un composant partagé.

## Organisation locale

`corpus_reel_candidats/` contient les fichiers ajoutés, inventaire.csv (vingt colonnes), catalogue CSV/JSON et sources précises. `L1_MaintiDoc_BELOUANAS_corpus/` est sa copie synchronisée pour la remise. Les noms des PDF sont conservés exactement. `images/fours/` et `images/serveurs/` contiennent 25 aperçus PNG de pages illustrées, reliés aux PDF dans les registres de traçabilité.

`docs/etat_corpus_reel.md` et `docs/corpus_actuel.json` décrivent le lot actif ; `docs/rapport_final.md` est la source du rapport ; `docs/diagrammes/` conserve les schémas. L’ancien lot synthétique est archivé, hors inventaire actif.

## Limites déclarées

Les 33 PDF portent le copyright fabricant ; aucune licence ouverte de redistribution du lot n’est établie. GitHub contient les liens et métadonnées, sans les PDF ou leurs rendus protégés. Le nombre de documents est atteint, mais la relecture humaine, les droits de remise, deux scans sources, une paire contradictoire et une note d’injection restent à traiter. Le rapport et le paquet local ne sont pas annoncés entièrement conformes au L1.

Le prototype logiciel n’est pas encore implémenté. Ressources déclarées : Mac i7, RAM 16 Go ; Windows Ryzen 7 5800X, RAM 32 Go, RTX 3080 10 Go de VRAM.
