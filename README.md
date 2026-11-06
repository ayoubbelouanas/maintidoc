# MAINTiDOC - Livrable 1

**Équipe : BELOUANAS - Ayoub BELOUANAS (individuel), EMSI.**
Préparation : 6 novembre 2026. Dépôt : https://github.com/ayoubbelouanas/maintidoc .

Assistant documentaire multimodal pour la maintenance de deux familles : fours mixtes professionnels RATIONAL et serveurs Dell PowerEdge, avec plusieurs modèles cibles. Question en français et photographie, réponse avec preuves, historique fictif via MCP et ticket seulement après approbation. Le prototype logiciel sera développé en semaines 2 à 6.

## Remise

Le ZIP `L1_MaintiDoc_BELOUANAS.zip` contient un dossier unique du même nom, avec quatre éléments : rapport PDF de 14 pages, lien GitHub, ce README et `L1_MaintiDoc_BELOUANAS_Corpus/`.

Le corpus contient **40 PDF (20 par famille)** : 30 documents synthétiques originaux et dix fiches avec photographies réelles sous droits spécifiques. Deux PDF image sont des scans simulés pour OCR ; quatre documents forment deux paires contradictoires ; deux notes piégées sont signalées. Aucun manuel fabricant sans permission de redistribution n'est inclus. Sources et conditions : `sources_et_droits.md`, inventaire et fiches photo.

## Structure du dépôt préparé

`docs/` : rapport source, contrôles et `diagrammes/` ; `corpus/` : `inventaire.csv` UTF-8 à vingt colonnes, `prompts_corpus.md`, sources et PDF dans `documents/fours/` et `documents/serveurs/` ; `.gitignore` exclut secrets et fichiers temporaires. Les codes MD-F et MD-S sont fictifs ; aucun document synthétique ne vaut procédure constructeur.

**Avant dépôt :** Ayoub doit relire les documents et renseigner les champs `verifie_par` et `corrections`. Ils restent vides tant que cette validation humaine n'est pas effectuée. La vérification technique de l'assistant ne la remplace pas. Le lien public fourni a été vérifié ; la publication des fichiers préparés est un contrôle distinct.

Matériel : Mac i7, RAM 16 Go ; Windows Ryzen 7 5800X, RAM 32 Go, RTX 3080 10 Go de VRAM. Les capacités du VLM et les performances n'ont pas encore été mesurées.
