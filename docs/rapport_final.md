# Rapport L1 - source de la version PDF


## 1. Cadrage du projet - MAINTiDOC

Cadrage, corpus et architecture | Module IA générative multimodale | EMSI



MAINTiDOC

Cadrage, corpus et architecture | Module IA générative multimodale | EMSI

Assistant documentaire multimodal et agentique pour la maintenance

| Équipe | BELOUANAS - travail individuel |

| Membre | Ayoub BELOUANAS |

| Enseignante | Mariam Cherrabi |

| Date de préparation | 6 novembre 2026 - échéance déclarée par l’étudiant |

| Familles | Fours mixtes professionnels RATIONAL ; serveurs Dell PowerEdge |

| Dépôt | https://github.com/ayoubbelouanas/maintidoc |

### But du prototype

But du prototype

Permettre à un technicien de poser une question en français avec une photographie, retrouver des preuves accessibles et préparer un ticket de maintenance. Le système distingue observation, source documentaire et historique fictif. Il demande une précision lorsque le modèle, le message ou les sources restent ambigus.

### Décision de périmètre

Décision de périmètre

Le projet couvre plusieurs modèles par famille. La remise locale comporte 40 PDF : 20 par famille, dont 10 fiches avec photographies réelles au total. Les procédures et données de simulation sont identifiées comme synthétiques ; elles ne sont pas des notices constructeur.

### État déclaré

État déclaré

Les fichiers et contrôles techniques de préparation sont réalisés par l’assistant. La relecture humaine du corpus n’est pas présumée : les champs verifie_par restent vides jusqu’à validation effective par Ayoub. Le projet logiciel n’est pas encore implémenté ; aucune performance n’est annoncée.

Référentiel : consignes L1 du 29 octobre 2026 et sujet MaintiDoc fournis par l’enseignante. Les six parties obligatoires sont présentées dans l’ordre ; les critères chiffrés d’évaluation du prototype seront définis en semaine 5.



## 1. Cadrage du projet - Utilisateurs et cas d’usage

Une organisation fictive possède deux parcs documentaires, avec accès distincts.



Utilisateurs et cas d’usage

Une organisation fictive possède deux parcs documentaires, avec accès distincts.

| Profil | Besoin | Accès |

| Technicien fours | Identifier une gamme, retrouver une source et préparer un signalement | techniciens_fours |

| Technicien informatique | Comprendre une observation matérielle et consulter un historique | techniciens_serveurs |

| Responsable maintenance | Consulter les deux périmètres explicitement partagés | responsables |

### Cinq parcours de démonstration

Cinq parcours de démonstration

| Cas | Demande et comportement attendu |

| CU01 - question et photo | Photo d’un four : décrire les indices visibles, demander le modèle s’il manque et citer la preuve documentaire disponible. |

| CU02 - historique | Photo de façade serveur : séparer ce qui est visible de l’historique obtenu par MCP pour l’identifiant interne confirmé. |

| CU03 - ticket | Préparer un brouillon avec équipement, titre, description et sources ; créer une seule fois après approbation du contenu exact. |

| CU04 - ambiguïté / versions | Image insuffisante ou règles contradictoires : signaler l’incertitude, comparer les versions et demander la précision utile. |

| CU05 - refus d’accès | Un technicien fours demande un document serveurs réservé : refuser texte, figure, extrait et ouverture directe. |

### Exemple de limite

Exemple de limite

Les photographies de fours de la gamme 5 Senses ne prouvent pas la taille 61 ni une option particulière. La bonne réponse peut donc être une demande de référence, et non l’attribution arbitraire à FOUR-RAT-02. Les identifiants AMB désignent uniquement des cas de test au modèle non établi.



## 1. Cadrage du projet - Objectifs, périmètre et contraintes





Objectifs, périmètre et contraintes

| Objectif en semaine 6 | Preuve attendue |

| Réponse fondée | Citations vers document, version, page et figure réellement récupérés ; appui vérifié. |

| Image exploitée | Observation distincte des déductions ; clarification si le modèle reste incertain. |

| Accès maîtrisé | Aucune fuite entre groupes, y compris via une URL de source ou une image extraite. |

| MCP utile | Historique et tickets liés au bon identifiant et autorisés côté serveur. |

| Ticket approuvé | Aucun appel créateur sans approbation valide ; répétition idempotente. |

| Robustesse | Cas ambigus, contradictoires et piégés testés séparément des cas d’entraînement. |

### Entrées, sorties et hors périmètre

Entrées, sorties et hors périmètre

Entrées : question en français, photographie, documents PDF. Sorties : réponse sourcée, clarification, refus, brouillon puis ticket approuvé. Outil externe : service MCP fictif de maintenance. Hors périmètre : pilotage d’une machine, diagnostic garanti et intervention autonome.

### Ressources réellement déclarées

Ressources réellement déclarées

Mac Intel Core i7 de 10e génération, RAM 16 Go ; poste Windows Ryzen 7 5800X, RAM 32 Go, RTX 3080 avec 10 Go de VRAM. Windows servira aux essais GPU. Aucun accès physique aux équipements n’est disponible. Ayoub réalise seul corpus, architecture, développement et évaluation.

### Hypothèses à mesurer

Hypothèses à mesurer

Le VLM proposé par le sujet est Qwen2.5-VL-7B-Instruct. Sa faisabilité avec quantification, la taille des images, le contexte et l’exécution séquentielle devront être mesurés sur les 10 Go de VRAM. Un modèle plus petit constitue le repli. Aucun débit ni temps de réponse n’est garanti au L1.



## 2. Constitution du corpus - Lot constitué et traçabilité

40 PDF présents ; 20 documents par famille ; un fichier correspond à une ligne d’inventaire.



Lot constitué et traçabilité

40 PDF présents ; 20 documents par famille ; un fichier correspond à une ligne d’inventaire.

| Propriété | Fours | Serveurs | Total |

| Documents | 20 | 20 | 40 |

| Documents synthétiques originaux | 15 | 15 | 30 |

| Fiches PDF avec photographie externe réelle | 5 | 5 | 10 |

| PDF image pour tester l’OCR | 1 | 1 | 2 |

| Versions volontairement contradictoires | 2 | 2 | 4 |

| Documents avec injection signalée | 1 | 1 | 2 |

| Documents contenant un visuel exploitable | 20 | 20 | 40 |

Les deux PDF image sont des scans simulés par rasterisation numérique des règles de suivi v1, sans couche texte. Ils testent l’OCR ; aucune acquisition papier n’est prétendue. Les tableaux et schémas originaux sont des visuels techniques synthétiques, distincts des dix photographies réelles.

### Variété et utilité

Variété et utilité

Chaque famille comprend registre, schéma de panneau, dictionnaire de messages fictifs, relevé initial, plan préventif documentaire, historique, deux versions d’une règle, note piégée, cas ambigu, fiche de sécurité, chaîne de citations, flux de ticket, matrice d’accès et recette. Les codes MD-F et MD-S ne sont pas des codes fabricants.

### Registre

Registre

inventaire.csv contient exactement les vingt colonnes requises. Provenance, licence, pages, visuels, usage de l’IA et groupes sont renseignés. Les photographies se trouvent dans leurs fiches PDF, sans fichier image supplémentaire compté comme un document distinct. verifie_par reste vide en attendant la relecture humaine effective.



## 2. Constitution du corpus - Modèles, preuves et droits





Modèles, preuves et droits

| Parc fictif | Cibles d’identification |

| FOUR-RAT-01 à 04 | iCombi Pro 6-1/1 électrique ; SCC 61 électrique ; iCombi Classic 6-1/1 électrique ; iHexagon 6-1/1 |

| SERV-DELL-01 à 05 | PowerEdge R720xd ; R730 ; R610 ; R710 ; R720 |

| FOUR-RAT-AMB / SERV-DELL-AMB | Images de famille ou de gamme dont le modèle exact n’est pas suffisamment établi |

### Sources réelles intégrées

Sources réelles intégrées

Dix photos Commons ont une provenance précise : Travelarz pour trois vues RATIONAL de salon, Pohled 111 pour deux vues en cuisine, Dell Inc. pour trois vues de serveurs, Toni Birrer pour la vue intérieure R610 et Dsv pour une vue de façades Dell. Une photo de salon est recadrée sur l’équipement afin d’exclure les personnes.

| Photos | Conditions de réutilisation retenues |

| 3 RATIONAL / Travelarz | CC BY-SA 3.0 Pologne : attribution et partage à l’identique des adaptations. |

| 2 RATIONAL / Pohled 111 | CC BY-SA 4.0 : attribution et partage à l’identique des adaptations. |

| 4 Dell / Dell Inc. et Toni Birrer | CC BY-SA 2.0 : attribution et partage à l’identique des adaptations. |

| 1 Dell / Dsv | Déclaration de mise dans le domaine public par l’auteur sur la fiche Commons. |

Les fiches livrées indiquent auteur, fichier source, URL de provenance, licence et transformation. La version de licence propre à chaque photographie est conservée. Les marques et les manuels fabricants ne deviennent pas libres parce qu’une photo est sous Creative Commons.

### Notices fabricants écartées de la redistribution

Notices fabricants écartées de la redistribution

L’audit RATIONAL a contrôlé 41 notices : 38 deviennent candidates avec le périmètre multi-modèles, deux concernent des hottes et une reste contradictoire. Aucune licence de redistribution du lot n’est établie : ces PDF restent hors ZIP et hors dépôt. Les accès directs Dell ont renvoyé HTTP 403 ; ils ne sont pas déclarés téléchargés.



## 2. Constitution du corpus - Usage critique de l’IA et relecture





Usage critique de l’IA et relecture

### Erreurs et corrections observées

Erreurs et corrections observées

La recherche initiale a confondu volume de liens PDF et volume de documents compatibles. Sur 41 notices RATIONAL, seules 14 correspondaient sous conditions aux deux premiers modèles électriques. L’élargissement à plusieurs gammes porte le nombre technique de candidats à 38, sans résoudre les droits. Cette correction évite de présenter un réservoir comme un corpus validé.

Certaines notices visent les appareils gaz, XS, au sol ou iHexagon. Les noms proches ne suffisent pas à établir la compatibilité. Les notices de réservoir/cartouches exigent la configuration correspondante ; aucune photo générale ne prouve AutoDose. MI_2511 comporte une incohérence entre les formats annoncés et un texte parlant de 20 niveaux : elle reste en quarantaine.

Des photos anciennes encore indexées étaient devenues indisponibles. Une fiche vendeur SCC61 se contredisait sur le nombre de phases. Une photo de pièce R730 démontre un panneau déposé, sans établir une panne ni un serveur alimenté. Les photos finales sont donc annotées selon leurs preuves, avec modèle inconnu lorsque nécessaire.

La licence d’une plateforme ne remplace pas celle d’un PDF tiers : des manuels Dell hébergés sur iFixit conservent leur copyright. Les conditions iFixit interdisent aussi l’entraînement de modèles sur leurs données. Aucun de ces documents n’a été intégré au corpus livré ni prévu pour le fine-tuning.

### Traçabilité et contrôles

Traçabilité et contrôles

prompts_corpus.md conserve les recherches antérieures et les nouveaux prompts P05 à P08. Pour chaque document, l’inventaire indique synthétique ou URL réelle, outil et prompt, droits, transformations et contrôles. Les messages, intervalles et identifiants fictifs sont cohérents entre les règles, versions et historiques.

### Validation humaine indispensable

Validation humaine indispensable

Les contrôles de l’assistant portent sur les fichiers, références, droits publiés et mise en page. Ils ne remplacent pas la relecture de l’équipe. Ayoub devra relire, corriger puis renseigner verifie_par et corrections. Aucun nom de relecteur ni résultat de test du prototype n’a été inventé.



## 3. Architecture cible - Blocs fonctionnels et contrôles

Schéma de haut niveau ; sources Mermaid conservées dans docs/diagrammes/.



Blocs fonctionnels et contrôles

Schéma de haut niveau ; sources Mermaid conservées dans docs/diagrammes/.

Depuis l’orchestration : recherche autorisée, analyse visuelle et consultation MCP, selon le besoin de la demande.

### Branche ingestion

Branche ingestion

### Branche outils

Branche outils

### Action sensible

Action sensible

Les flèches représentent respectivement question et identité ; candidats et preuves ; réponse et citations ; éléments indexés et métadonnées ; paramètres et résultats d’outil ; contenu approuvé et clé d’idempotence. Les autorisations sont revérifiées à l’ouverture des originaux et côté MCP.

La validation des citations combine existence du document, localisation et appui de l’affirmation. Une vérification de format seule ne garantit pas une réponse fondée.



## 3. Architecture cible - Fiches des blocs et hypothèses





Fiches des blocs et hypothèses

| Bloc / outil envisagé | Entrées → sorties et rôle |

| Interface - Streamlit | Question, image, approbation → requête et réponse lisible avec sources. |

| API - FastAPI | Identité et requête → opération autorisée et groupes fiables, ou refus. |

| Orchestration - LangGraph / LangChain | Demande autorisée et état → parcours de recherche, appel MCP ou clarification. |

| Ingestion - PyMuPDF / OCR local | PDF et inventaire → passages, tableaux, figures et métadonnées. |

| Recherche - Qdrant / encodeurs | Question, image et ACL → candidats texte/image ; fusion de rangs possible. |

| Reranker multilingue | Question et passages autorisés → classement ; adaptation ciblée en S5. |

| VLM - Qwen2.5-VL-7B envisagé | Image et preuves → observations et réponse proposée ; modèle inchangé. |

| Validation - Pydantic + contrôles | Réponse et preuves → réponse sourcée, abstention ou clarification. |

| MCP de démonstration | Identité, équipement et paramètres → historique, tickets, création approuvée. |

| Stockage - PostgreSQL / MinIO | Métadonnées, originaux et événements → données persistantes autorisées. |

### Points à vérifier en semaines 2 et 3

Points à vérifier en semaines 2 et 3

Fixer les versions et licences des outils ; mesurer mémoire et latence sur la RTX 3080 10 Go ; choisir l’OCR et la stratégie de découpage ; tester embeddings texte et image ; contrôler l’appui sémantique des citations et la reprise après attente d’approbation. L1 n’annonce aucune compatibilité mesurée.



## 4. Flux de données - Ingestion et métadonnées





Ingestion et métadonnées

### Étapes et contrôles

Étapes et contrôles

1. Vérifier présence du fichier, licence, provenance et validation humaine. Refuser un document absent de l’inventaire ou sans groupe d’accès.<br/>2. Conserver l’original et son empreinte ; détecter PDF texte ou PDF image.<br/>3. Extraire texte, tableaux et figures. L’OCR fournit texte et positions pour les deux scans simulés.<br/>4. Découper en passages et éléments visuels, en conservant la page PDF physique et les renvois.<br/>5. Calculer les représentations textuelles et visuelles puis indexer avec les ACL héritées. Les fichiers de test restent identifiés.

| Métadonnée d’un élément | Exemple concret du corpus |

| document_id / version | fours_codes / v1 (2026-11-06) |

| page / element_id / type | 1 / tableau_1 / tableau |

| famille_equipement | fours_mixtes_professionnels |

| equipement_ids | FOUR-RAT-01 à FOUR-RAT-04, selon le registre |

| groupes_acces | techniciens_fours ; responsables |

| source_file | documents/fours/fours_codes.pdf |

| usage_test / provenance | normal / synthetique |

| empreinte et extraction | SHA-256 du fichier ; OCR ou texte, avec confiance si disponible |

Une nouvelle version reçoit un identifiant ou une version distincte. Les versions v1 et v2 contradictoires restent disponibles pour comparaison ; le contenu ancien n’est pas silencieusement écrasé.



## 4. Flux de données - Requête et contrôle d’accès





Requête et contrôle d’accès

### Parcours complet

Parcours complet

1. L’API authentifie l’utilisateur fictif et obtient ses groupes côté serveur.<br/>2. Le VLM décrit les indices visibles sans attribuer une cause non observée.<br/>3. Si l’équipement n’est pas établi, le workflow demande sa référence avant toute procédure spécifique.<br/>4. Les recherches textuelle et visuelle portent uniquement sur les documents autorisés ; les candidats sont fusionnés et reclassés.<br/>5. Un appel MCP utile consulte l’historique de l’équipement confirmé, après autorisation côté outil.<br/>6. Le VLM rédige une proposition à partir des preuves. Le validateur contrôle document, version, page et appui.<br/>7. L’interface affiche la réponse, les limites et les sources ; leur ouverture déclenche un nouveau contrôle d’accès.

| Groupe | Périmètre autorisé |

| techniciens_fours | Documents fours normaux et ambigus explicitement partagés ; pas les notes piégées réservées. |

| techniciens_serveurs | Documents serveurs normaux et ambigus explicitement partagés ; pas les documents fours. |

| responsables | Deux parcs explicitement partagés, y compris les deux notes de test réservées. |

| Groupe absent / inconnu | Refus par défaut ; aucune déduction de droits à partir d’un texte de document. |

### Illustration d’un refus

Illustration d’un refus

Un utilisateur techniciens_fours demande serveurs_historique : la recherche ne lui renvoie ni extrait ni figure. Une requête directe vers le PDF ou son image extraite reste refusée. Le service MCP applique ses propres contrôles même si la recherche a déjà filtré le corpus.



## 4. Flux de données - Création de ticket et cohérence des outils





Création de ticket et cohérence des outils

| État | Données et contrôle |

| Préparé | Identifiant interne confirmé, titre, description, preuves et champs manquants. Aucune création. |

| Présenté | L’utilisateur voit le contenu exact et peut le modifier ou refuser. |

| Approuvé | Associer utilisateur, équipement, contenu canonique et empreinte au consentement. |

| Vérifié par MCP | Vérifier droits, approbation, contenu inchangé et clé d’idempotence avant l’écriture. |

| Créé / rejoué | Conserver ticket et clé ; une répétition renvoie le résultat existant. |

| Modifié / expiré / refusé | Invalider l’approbation et revenir à la présentation ; ne pas appeler la création. |

### Contrats d’outils envisagés

Contrats d’outils envisagés

get_equipment_history(equipment_id) renvoie les événements autorisés ; list_open_tickets(equipment_id) renvoie les tickets déjà ouverts ; create_ticket(equipment_id, title, description, approval_token, idempotency_key) crée seulement après contrôles serveur. Ces noms décrivent le contrat cible, pas une API déjà développée.

### Invariant de sécurité

Invariant de sécurité

Une instruction trouvée dans une notice, une photographie, un OCR ou un résultat d’outil n’est jamais une approbation. Le LLM ne choisit ni ses groupes d’accès ni la validité du jeton. Les journaux doivent enregistrer les décisions sans exposer de secrets ou de données réelles.



## 5. Analyse des risques - Risques et mesures initiales

Échelles : probabilité et impact de 1 (faible) à 3 (élevé). Responsable : Ayoub BELOUANAS pour chaque ligne.



Risques et mesures initiales

Échelles : probabilité et impact de 1 (faible) à 3 (élevé). Responsable : Ayoub BELOUANAS pour chaque ligne.

| Risque / catégorie | P | I | Mesure prévue | Resp. |

| Hallucination / technique | 2 | 3 | Contrôler appui et citations ; tester abstention et questions sans source. | Ayoub |

| Fuite entre groupes / sécurité | 2 | 3 | Filtre avant recherche, ouverture protégée, contrôle MCP. | Ayoub |

| Ticket non approuvé / sécurité | 2 | 3 | Approbation serveur liée au contenu exact et à l’utilisateur. | Ayoub |

| Ticket dupliqué / technique | 2 | 2 | Idempotence côté stockage et tests de répétition. | Ayoub |

| Injection de prompt / sécurité | 2 | 3 | Documents traités comme données ; outils limités ; tests réservés. | Ayoub |

| Erreur IA / données | 3 | 3 | Codes MD fictifs, registre commun, relecture humaine réelle. | Ayoub |

| Droits de réutilisation / données | 2 | 3 | Exclure les notices protégées ; attribution des photos et licences propres. | Ayoub |

| Mémoire GPU insuffisante / technique | 2 | 3 | Mesurer tôt ; quantifier et prévoir un VLM plus petit. | Ayoub |

| OCR erroné / données | 2 | 2 | Comparer au PDF image, conserver positions et signaler l’incertitude. | Ayoub |

| Confusion modèle/version / données | 3 | 3 | Filtrer la configuration ; comparer versions ; demander le modèle. | Ayoub |

| Fuite entraînement/test / données | 2 | 3 | Séparer les documents avant génération des triplets du reranker. | Ayoub |

| Délai et relecture / organisation | 3 | 3 | Limiter à 40 documents, suivre les contrôles et réserver la validation finale. | Ayoub |

Ces scores sont des estimations de cadrage et non des résultats d’expérience. Le suivi de chaque risque sera mis à jour pendant les semaines 2 à 6, avec les incidents rencontrés et la mesure appliquée.



## 6. Planning et organisation - Responsabilités et semaines 2 à 6





Responsabilités et semaines 2 à 6

| Fonction | Membre / tâches |

| Coordination et rapport | Ayoub BELOUANAS : périmètre, planning, suivi des risques et remise. |

| Corpus et ingestion | Ayoub : relecture, corrections, inventaire, OCR et découpage. |

| Architecture et sécurité | Ayoub : authentification, ACL, contrats MCP et approbation. |

| Expérimentation et évaluation | Ayoub : mesures matérielles, reranker, tests et soutenance. |

| Semaine | Travail et résultat attendu |

| S2 | Figer outils et versions ; valider corpus ; extraction/OCR ; index et permissions. Résultat : éléments recherchables avec métadonnées complètes. |

| S3 | Intégrer VLM, recherche image et citations. Résultat : réponse texte/photo sourcée avec clarification en cas d’incertitude. |

| S4 | Orchestrer LangGraph et MCP ; approbation et idempotence. Résultat : historique et ticket contrôlés de bout en bout. |

| S5 | Préparer 800 à 1 500 triplets synthétiques vérifiés, séparés par document ; adapter uniquement le reranker. Comparer sans reranker, initial et adapté. |

| S6 | Déployer et mesurer, corriger les défauts, documenter les limites et préparer la démonstration. |

### Évaluation prévue

Évaluation prévue

Définir en S5 les seuils et jeux de test. Mesurer nDCG@5 et MRR@10 pour le classement, qualité de l’appui documentaire, refus intergroupes, résistance aux injections et absence de création non approuvée. Rapporter les résultats même si le fine-tuning n’améliore pas le classement.

Les deux notes piégées, les quatre versions contradictoires et les photographies ambiguës servent à des tests réservés. Les images et textes tiers ne sont pas utilisés pour entraîner le modèle vision-langage, qui reste inchangé.



## 6. Planning et organisation - Remise, contrôles et limites déclarées





Remise, contrôles et limites déclarées

| Élément requis | Nom / état de préparation |

| Archive | L1_MaintiDoc_BELOUANAS.zip |

| Dossier racine | L1_MaintiDoc_BELOUANAS/ - quatre éléments seulement |

| Rapport | L1_MaintiDoc_BELOUANAS_Rapport.pdf - 14 pages prévues |

| Lien GitHub | L1_MaintiDoc_BELOUANAS_LienGitHub.txt - URL fournie par Ayoub |

| README | README.md - membre, objectif, contenu et structure |

| Corpus | L1_MaintiDoc_BELOUANAS_Corpus/ - 40 PDF, inventaire, prompts et registre des droits |

### Contrôles techniques à consigner

Contrôles techniques à consigner

Vérifier noms et arborescence du ZIP, correspondance bijective fichiers/inventaire, empreintes distinctes, nombre de pages, absence de couche texte dans les deux PDF image, licences et attributions, rendu du rapport et absence de secrets. Le résultat réel est enregistré dans docs/controle_livraison.json après génération ; cette page ne prétend pas anticiper un test non exécuté.

### Deux étapes humaines avant le dépôt

Deux étapes humaines avant le dépôt

1. Relire et corriger les documents puis compléter verifie_par et corrections. Les champs de relecture sont volontairement vides au moment de la préparation.<br/>2. Publier les fichiers préparés dans le dépôt GitHub fourni et vérifier son contenu depuis un compte extérieur. L’URL répond publiquement, mais cela ne prouve pas que les fichiers de cette remise y ont été envoyés.

### Sources et audit

Sources et audit

Le journal du corpus liste les sources précises et les conditions de réutilisation. Les fiches photographiques portent leurs liens de licence. Les audits de recherche et les sources des schémas restent dans docs/ ; les notices fabricants sans permission de redistribution sont exclues de l’archive et du dépôt préparé.

Dépôt de l’équipe : <link href="https://github.com/ayoubbelouanas/maintidoc" color="#087E8B">github.com/ayoubbelouanas/maintidoc</link><br/>Référentiel pédagogique : L1, 29 octobre 2026, Mariam Cherrabi. Date de remise déclarée : 6 novembre 2026 ; aucune heure limite n’a été fournie.
