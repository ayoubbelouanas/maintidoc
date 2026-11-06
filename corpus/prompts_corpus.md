# Traçabilité des prompts du corpus

Statut : aucun document n'a encore été intégré au corpus ni validé par l'équipe.
Un premier repérage de sources publiques a été réalisé ; voir P01 ci-dessous.
Les documents proposés dans `docs/plan_corpus.md` sont un plan, pas un corpus constitué.

Pour chaque usage effectif de l'IA, conserver le texte exact du prompt, l'outil et
la date réelle. Numéroter les entrées P01, P02, etc. Réutiliser ces références dans
la colonne `outil_ia` de l'inventaire. Ne pas inventer de relecture humaine,
de correction, de licence vérifiée ou de source consultée.

Chaque entrée devra contenir :

- Identifiant du prompt.
- Date réelle, outil et modèle si connu.
- Objectif et texte exact du prompt.
- Identifiants des documents concernés.
- Résultat obtenu, erreurs observées et corrections réellement effectuées.
- Personne ayant relu et validé les documents, une fois cette validation faite.

## Analyse critique à préparer

Le rapport final inclura environ une demi-page sur les erreurs réellement repérées
pendant la constitution du corpus : incohérences d'identifiants, unités, codes
d'alarme, renvois de pages, images, liens ou conditions de réutilisation.
Une contradiction volontaire et une injection volontaire sont des cas de test ;
elles doivent être distinguées des erreurs accidentelles corrigées.

## P01 — Repérage de familles et de documentations

- Date : 30 octobre 2026.
- Outil : assistant Codex et recherche web ; modèle non consigné.
- Demande utilisateur exacte : « donne moi d'abord qu'elles sonts les familles d'equipements qui ont des documentations et des livres de maintenance et quelles sont ses equipements ? »
- Objectif : comparer des familles avant de choisir les deux familles du corpus.
- Requêtes exécutées, conservées textuellement :

```text
site.grundfos.com CR CRE installation operating instructions maintenance pdf
site.atlascopco.com compressor instruction book maintenance GA
site.se.com Altivar ATV320 programming installation manual
site.cummins.com generator operator manual maintenance
CR CRI CRN notice installation fonctionnement maintenance français
Smart UPS SMT user manual français remplacement batterie
S7 1200 system manual diagnostics maintenance
compresseur CSG notice utilisation entretien français
ATV320 guide programmation NVE41296 français
```

Les requêtes 5 à 8 ont été filtrées sur les domaines fabricants pertinents ;
la requête 9 a été filtrée sur `se.com`.
Résultats et liens : `docs/choix_equipements.md`.
Documents du corpus concernés : aucun à ce stade.
Vérification humaine et licences de réutilisation : non réalisées.
Observations : certains résultats initiaux provenaient de sites tiers et de forums ;
seules des sources fabricants ont été retenues dans la comparaison. Une tentative
d'ouverture du PDF Grundfos 3929729 par l'outil web a échoué en raison de sa taille.
Le catalogue de sources ne prouve donc pas la lecture intégrale ni l'autorisation
de redistribution de ces documents.

## P02 — Benchmark des familles, des PDF et des photos

- Période : recherche à partir du 30 octobre 2026, audit visuel local terminé le 1er novembre 2026.
- Outil : assistant Codex, recherche web, téléchargement autorisé de dix notices et Poppler pour la lecture et le rendu.
- Demande utilisateur exacte : « donne moi un benchmark depuis ces derniers resultats en prenant en consideration l’accès à de **vraies photos de panneaux ou d’équipements et la disponibilité de 30 jusqu'à 50 documents pdfs pour la maintenance que je peux donner au system rag pour chaque familles d'equipements** »
- Précisions exactes : « aucun acces pour le moment » ; « parmi les 30-50 pdfs , j'ai besoin de 10 pdfs contenant les images ».
- Objectif : comparer les huit familles déjà proposées sans présumer des droits de réutilisation ni du choix final.
- Résultats et références : `docs/benchmark_familles.md` et `docs/recherche/`.
- Documents intégrés au corpus : aucun. Les dix téléchargements sont temporaires et réservés à la vérification.
- Contrôles réalisés par l'assistant : 61 liens RATIONAL testés, 41 URL PDF reconnues, puis dix fichiers aux empreintes différentes téléchargés, rendus et inspectés sur une page de contenu chacun. Les visuels observés sont des figures techniques ; aucune relecture humaine ni licence approuvée n'est déclarée.
- Analyse critique factuelle : une recherche « Sunny Boy » a renvoyé une statue et une recherche « John Deere dashboard » une voiture portant un logo ; ces résultats ont été exclus. Les photos Zebra de modèles de bureau ou mobiles ne prouvent pas l'accès à des photos du modèle industriel ZT411. Certains manuels regroupent plusieurs modèles ou ont plusieurs traductions. Plusieurs notices RATIONAL réemploient des figures communes. Les versions du cache web et des fichiers téléchargés peuvent différer.
- Questions ouvertes : pertinence finale de chaque PDF, modèle exact des photos, droits de réutilisation et relecture par Ayoub.

## P03 — Présélection des modèles

- Date : 1er novembre 2026.
- Outil : assistant Codex et recherche web sur les sites fabricants et les pages de médias Commons.
- Demande utilisateur exacte : « aide moi à choisir les modeles ».
- Objectif : proposer un périmètre de modèles limité pour les deux familles retenues.
- Résultat : `docs/choix_modeles.md`, avec les références et limites ; présélection iCombi Pro 6-1/1, SelfCookingCenter 61, Dell PowerEdge R720xd et R730.
- Vérification : notices et manuels repérés ; photo attribuée au R720xd sous CC BY-SA 2.0. Les photos de la gamme SelfCookingCenter ne prouvent pas le format 61 exact. Aucune photo libre du R730 exact n'est confirmée. Un résultat de recherche sur une fiche technique Dell hébergée dans un autre service n'est pas traité comme preuve d'une licence propre au PDF ou d'une photo.
- Documents intégrés ou validés humainement : aucun. La compatibilité des PDF du benchmark avec cette présélection doit être recomptée ; les licences restent à examiner avant intégration.


## P04 — Audit intégral de compatibilité et des photos

- Date : 1er novembre 2026.
- Demande exacte : « je trouves que tu me laisse confirmer plusieurs choix , cherche et donne moi le resultat , je veux du concret , cherche la disponibilité des photos et si les 41 pdfs sont compatibles ou pas ».
- Outils : recherche web, navigateur, curl, pdfinfo, pdftotext, rendu Poppler et lecture visuelle des pages de périmètre et de figures. Les 41 PDF ont été téléchargés temporairement, identifiés par empreinte SHA-256 et confrontés aux deux modèles électriques retenus.
- Résultat : 14 retenables sous conditions, 26 exclus, MI_2511 en quarantaine pour contradiction entre tailles indiquées. Douze documents retenables ont une page illustrée vérifiée. Sept notices de nettoyage nécessitent l'option correspondante ; TI_2321 confirme les conditions AutoDose d'usine.
- Résultats détaillés et preuves : `docs/recherche/compatibilite_41_rational.json`, `.md` et `docs/recherche/audit_photos_modeles.md`.
- Analyse critique : anciennes photos RATIONAL indexées mais indisponibles écartées ; deux images SCC61 accessibles mais fiche vendeur contradictoire sur le nombre de phases ; panneau R730 réel mais déposé, non représentatif d'une panne ; photo Commons R720xd attribuée par le nom de fichier, licence vérifiée ; photo 5Senses libre mais format61 non établi.
- Corpus final : aucun document intégré ; fichiers téléchargés conservés dans tmp ignoré par Git pour l'audit. Relecture humaine non réalisée. Les licences ouvertes trouvées concernent certaines photos, pas les notices PDF ni toutes les photos vendeurs.

## P05 — Élargissement du périmètre et préparation à l’échéance

- Date : 6 novembre 2026 ; outil : Codex, recherche web, curl et Poppler.
- Demande utilisateur exacte : « on va travailler sur plusieurs models pour chaque famille pour avoir plus de documents ( entre 30 et 50 pdfs avec 10 parmi eux en photos ) et je voudrais qu'on termine ce livrable aujourdhui car c'est le délai ».
- Clarification exacte : « non je veux 30 à 50 au total et il faut que la source soit précise ( pdf fabricants utilisable , ou synthetique mais preferable qu'il soient reels) ».
- URL fournie par l'utilisateur : https://github.com/ayoubbelouanas/maintidoc .
- Décision de construction : 40 PDF, 20 par famille. Privilégier les sources réelles réutilisables ; exclure de la redistribution les notices fabricants dont la permission n'est pas établie. Créer les documents fictifs nécessaires en les signalant explicitement.
- Résultat critique : 38 notices RATIONAL candidates après élargissement, deux notices de hottes hors sélection, une en quarantaine. Aucun de ces 41 PDF n'est intégré à la remise faute de permission de redistribution établie. Les 30 essais directs Dell ont renvoyé HTTP 403, sans preuve que les URL seraient invalides ; aucun téléchargement n'est compté comme réussi.
- Une recherche iFixit a trouvé des documents Dell tiers qui conservent leur copyright ; la licence de la plateforme n'est pas appliquée abusivement à ces PDF. L'interdiction d'entraînement publiée par iFixit a également conduit à exclure ces contenus de la préparation du fine-tuning.

## P06 — Génération du jeu documentaire synthétique original

- Date : 6 novembre 2026 ; outil : Codex et ReportLab ; fichiers concernés : les 30 PDF dont provenance = synthetique.
- Instruction de génération effectivement mise en œuvre : « Constituer pour chacune des deux familles 15 documents originaux de démonstration : registre, panneau schématique, codes fictifs, relevé initial, plan de suivi, historique, deux versions contradictoires d'une règle, note d'injection isolée, ambiguïté, sécurité, citations, ticket, ACL et recette. Utiliser les identifiants FOUR-RAT-01 à 04 et SERV-DELL-01 à 05, et des codes MD-F/MD-S explicitement fictifs. Aucun code, réglage, couple ou procédure constructeur ne doit être inventé comme réel. Les contradictions concernent uniquement une revue documentaire chaque jour en v1 / chaque lundi en v2. Fournir pages et figures identifiables. »
- Fabrication : deux pages par document ; deux versions v1 rasterisées sans couche texte pour tester l'OCR. Il s'agit de scans simulés, pas d'une acquisition papier.
- Corrections réellement effectuées : en-têtes des versions v1/v2 harmonisés avec leurs dates et avec l'inventaire ; les codes fictifs et les limites de chaque procédure restent affichés. Les notes d'injection sont réservées au groupe responsables et étiquetées injection.
- Droits : documents synthétiques originaux autorisés pour le projet ; aucun extrait ni schéma de fabricant reproduit. Les marques nomment seulement les cibles du parc fictif.
- Contrôle assistant réalisé : génération, cohérence des références, mise en page, nombre de pages et absence de couche texte des PDF image.
- Relecture humaine : non effectuée par l'assistant et non attribuée à Ayoub par anticipation ; verifie_par reste vide.

## P07 — Fiches de photographies réelles sous droits explicites

- Date : 6 novembre 2026 ; outil : Codex, Commons, curl, ReportLab et inspection visuelle.
- Instruction de transformation : « Sélectionner dix photographies réelles réutilisables, cinq fours RATIONAL et cinq serveurs Dell ; préserver les licences propres, créditer l'auteur et fournir le lien exact du fichier. Décrire uniquement les éléments prouvés et signaler modèle inconnu, sans inventer de code de panne. Produire une fiche PDF par photo, sans compter deux fois la source comme fichier image indépendant. Exclure les personnes du cadrage livré. »
- Sources exactes, auteurs, licences et transformations : voir `sources_et_droits.md` dans ce dossier, inventaire.csv et chaque fiche PDF.
- Transformations : mise à l'échelle et légende en français. La photo fours_photo_01 est recadrée sur l'appareil ; les personnes du stand et de son arrière-plan sont exclues. Les cinq vues par famille ne constituent pas forcément cinq équipements distincts : les photos de gamme et les vues rapprochées restent signalées.
- Corrections : une photo CC0 alternative de faible résolution a été envisagée mais n'a pas été téléchargée à cause d'une limitation HTTP 429 ; elle n'est pas comptée dans les dix fichiers livrés. Les licences de pied de page Commons sur les métadonnées ne sont pas confondues avec les licences des images.
- Relecture humaine : à réaliser ; contrôle de l'assistant distinct de la validation de l'équipe.

## P08 — Rapport et packaging

- Date : 6 novembre 2026 ; outil : Codex, ReportLab, Poppler et pypdf.
- Instruction mise en œuvre : « Produire un rapport français de 10 à 15 pages couvrant les six parties obligatoires dans l'ordre ; indiquer les volumes réels, les limites de la réutilisation, l'architecture, les trois flux, les ACL, au moins huit risques et l'organisation S2–S6. Ne déclarer ni validation humaine ni performance du prototype non réalisée. Préparer le ZIP selon les quatre éléments imposés et vérifier la bijection entre inventaire et fichiers. »
- Le journal des contrôles techniques est conservé dans docs/controle_livraison.json dans les sources préparées pour GitHub. La relecture humaine et l'état réel de publication restent déclarés séparément.

- Contrôles finaux supplémentaires : correction d’un motif de code non résolu dans les clés du tableau des messages ; les codes MD-F/MD-S ont été réinspectés dans les PDF. Le contrôle des sections du rapport a été rendu insensible à la casse des en-têtes. Une colonne de responsable a été ajoutée au tableau des risques.
- Publication : les fichiers préparés ont été envoyés sur `codex/livraison-l1` dans le dépôt GitHub fourni ; la connexion Git existante du poste a permis l’envoi. Aucune clé ni aucun jeton n’a été affiché ou copié dans le projet.
