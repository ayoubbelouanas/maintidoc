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

Le projet couvre plusieurs modèles par famille. Le corpus local comporte 33 PDF fabricants : vingt notices RATIONAL et treize documents Dell. Il comprend dix manuels propriétaires Dell, deux guides techniques et un guide RAID PERC 9. Trois documents synthétiques de test S5 s’ajoutent à ces sources, portant le total à 36 PDF : une paire contradictoire et une note piégée. Ils ne remplacent aucun manuel fabricant. Les noms de fichiers téléchargés sont conservés exactement dans l’inventaire.

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

Une vue de châssis ou une désignation de gamme ne prouve pas la configuration complète. Le RAG doit distinguer R720 de R720xd, iCombi Pro d’iCombi Classic et le composant PERC 9 du serveur qui l’héberge. La référence documentaire ne représente pas un numéro de série ni un équipement réel accessible à l’équipe.



## 1. Cadrage du projet - Objectifs, périmètre et contraintes





Objectifs, périmètre et contraintes

| Objectif en semaine 6 | Preuve attendue |

| Réponse fondée en français | Réponse française même si la preuve est anglaise ; citation de la source originale, page et appui vérifiés. |

| Image exploitée | Observation distincte des déductions ; clarification si le modèle reste incertain. |

| Accès maîtrisé | Aucune fuite entre groupes, y compris via une URL de source ou une image extraite. |

| MCP utile | Historique et tickets liés au bon identifiant et autorisés côté serveur. |

| Ticket approuvé | Aucun appel créateur sans approbation valide ; répétition idempotente. |

| Robustesse | Cas ambigus, contradictoires et piégés testés séparément des cas d’entraînement. |

### Entrées, sorties et hors périmètre

Entrées, sorties et hors périmètre

Entrées : question en français, photographie, documents PDF. Sorties : réponse sourcée en français par défaut, clarification, refus, brouillon puis ticket approuvé. Une réponse en anglais peut être demandée explicitement. Outil externe : service MCP fictif de maintenance. Hors périmètre : pilotage d’une machine, diagnostic garanti et intervention autonome.

### Ressources réellement déclarées

Ressources réellement déclarées

Mac Intel Core i7 de 10e génération, RAM 16 Go ; poste Windows Ryzen 7 5800X, RAM 32 Go, RTX 3080 avec 10 Go de VRAM. Windows servira aux essais GPU. Aucun accès physique aux équipements n’est disponible. Ayoub réalise seul corpus, architecture, développement et évaluation.

### Hypothèses à mesurer

Hypothèses à mesurer

Le VLM proposé par le sujet est Qwen2.5-VL-7B-Instruct. Sa faisabilité avec quantification, la taille des images, le contexte et l’exécution séquentielle devront être mesurés sur les 10 Go de VRAM. Un modèle plus petit constitue le repli. Aucun débit ni temps de réponse n’est garanti au L1.



## 2. Constitution du corpus - 36 PDF : sources réelles et tests S5

Comptage fondé sur les fichiers locaux et leur contenu, pas sur les liens proposés.



36 PDF : sources réelles et tests S5

Comptage fondé sur les fichiers locaux et leur contenu, pas sur les liens proposés.

| Nature | RATIONAL | Dell | Total |

| Notices de maintenance | 20 | 0 | 20 |

| Manuels propriétaires | 0 | 10 | 10 |

| Guides techniques R720/R720xd et R730/R730xd | 0 | 2 | 2 |

| Guide du composant RAID PERC 9 | 0 | 1 | 1 |

| PDF réels présents | 20 | 13 | 33 |

| Tests synthétiques S5 | 1 | 2 | 3 |

| Total des PDF actifs | 21 | 15 | 36 |

| Aperçus de PDF fabricants | 12 | 13 | 25 |

Langues : les 13 PDF Dell sont en anglais (langue = en dans l’inventaire). Les notices RATIONAL ont le français comme langue principale ; MI_2208 est multilingue avec une section française p.17 à 24. Les sources ne sont pas remplacées par une traduction.

### Trois ajouts effectivement contrôlés

Trois ajouts effectivement contrôlés

Le guide technique R720/R720xd comporte 65 pages ; celui du R730/R730xd, 66 pages ; le guide PERC 9, 128 pages. Leurs titres ont été lus dans les fichiers fournis par Ayoub. Les guides iDRAC7, iDRAC8 et Lifecycle Controller proposés mais non ajoutés sont exclus du comptage et de l’inventaire actif.

### Registre et noms des sources

Registre et noms des sources

inventaire.csv comporte les vingt colonnes requises, une ligne par PDF présent et les chemins exacts, y compris espaces et apostrophes. Le document_id reste un identifiant stable normalisé ; le champ fichier conserve le nom réellement téléchargé. Les pages, versions, séries, provenance et droits proviennent des fichiers ou de leurs sources identifiées.

### Visuels et pages blanches

Visuels et pages blanches

Vingt-cinq aperçus PNG de pages illustrées réelles sont disponibles : douze RATIONAL et treize Dell. Les registres images/tracabilite_images.csv et JSON relient chaque aperçu au PDF, à sa page physique, à sa source et à ses empreintes. Ces aperçus ne sont pas des photographies isolées et ne sont pas comptés comme vingt-cinq documents supplémentaires. Les pages blanches restent dans les originaux ; elles seront ignorées à l’indexation.



## 2. Constitution du corpus - Séries et composants documentés





Séries et composants documentés

| Périmètre réel | Documents et limite |

| RATIONAL : iCombi Pro | Notices de nettoyage, réservoir/cartouches, vitrage, ventilation et éclairage selon la notice et les options. |

| RATIONAL : iCombi Classic | Notices partagées de vitrage, éclairage, ventilation et optimisation électrique ; ne pas étendre les notices Pro seules. |

| RATIONAL : SelfCookingCenter | Pompe UP30, CareControl TG, détartrant pour indices H/I et éclairage selon la notice. |

| RATIONAL : iHexagon | Six notices de composants : filtration, Magnetron, sonde, alimentation et ventilation. |

| Dell : dix manuels propriétaires | R220, R230, R320, R430, R520, R530, R620, R720/R720xd, T320 et T330. |

| Dell : deux guides techniques | R720/R720xd et R730/R730xd ; aucun manuel propriétaire R730/R730xd n’a été ajouté. |

| Dell : PERC 9 | Un guide du contrôleur RAID ; ce composant ne constitue pas un modèle supplémentaire de serveur. |

### Treize désignations de serveurs

Treize désignations de serveurs

R220, R230, R320, R430, R520, R530, R620, R720, R720xd, R730, R730xd, T320 et T330 sont documentés, avec une profondeur différente selon le type de guide. R610, R710 et T630 ne font pas partie du corpus technique actif. Les références DELL_* et RAT_* servent aux métadonnées ; ce ne sont pas des numéros de série.

### Applicabilité par document

Applicabilité par document

Les formats, l’énergie, les indices, les références de pièces et les options restent associés à chaque notice. Le système ne doit pas appliquer une notice iHexagon à un iCombi Pro, une procédure électrique à la variante gaz, ni un guide PERC 9 à une carte d’une autre génération. La ligne MI_2505 précise que la seule mention SCC dans son titre ne prouve pas son inclusion dans la rubrique produit.



## 2. Constitution du corpus - Traçabilité, droits et limites actuelles





Traçabilité, droits et limites actuelles

### Source réelle et assistance IA

Source réelle et assistance IA

Les 33 PDF fabricants restent inchangés et genere_par_ia y vaut non. Les trois documents S5 ajoutés sont des créations synthétiques originales, signalées oui et liées au prompt P14. L’assistant a aidé à rechercher les sources, contrôler les noms, titres, pages et empreintes, puis produire les métadonnées et les aperçus. Il n’a pas réécrit les manuels. Les prompts historiques sont conservés et les corrections et ajouts sont tracés dans P10 à P14.

### Correction du travail antérieur

Correction du travail antérieur

L’ancien lot principalement synthétique a été rejeté par Ayoub. Il est archivé séparément et n’alimente plus l’inventaire actif. La présente révision utilise uniquement les fichiers réellement ajoutés. Les trois guides Dell supplémentaires non téléchargés sont explicitement hors sélection ; aucun téléchargement absent n’est présenté comme accompli.

### Droits de réutilisation

Droits de réutilisation

Disponibilité publique et licence ouverte sont distinctes. Les PDF portent le copyright RATIONAL ou Dell ; aucune permission générale de redistribution n’est établie pour ce lot. Les fichiers et leurs rendus restent locaux. GitHub publie le rapport, les liens et métadonnées, ainsi que les trois PDF de test originaux. Il ne redistribue pas les fichiers fabricants. La conformité juridique du corpus remis reste à établir selon l’usage autorisé.

### Exigences L1 non encore satisfaites

Exigences L1 non encore satisfaites

| Exigence | État du lot réel actuel |

| 30 à 50 documents, deux familles | 36 PDF présents : 33 fabricants et trois tests synthétiques. |

| Au moins dix documents avec visuels | 25 pages illustrées repérées et rendues, sur 25 PDF distincts. |

| Deux documents scannés pour OCR | Aucun scan identifié et validé dans ce lot ; ne pas compter les pages blanches ou les aperçus PNG comme des scans. |

| Deux documents contradictoires et une injection | Paire de procédures R720/R720xd v1/v2 : revue toutes les 24 h / tous les 7 jours, dates explicites. Note iCombi Pro : injection p.2. Étiquettes dans l’inventaire ; scénarios S5 préparés, non exécutés. |

| Relecture humaine | Champs verifie_par vides tant qu’Ayoub n’a pas validé chaque document. |

Les trois PDF sont réservés au split test_s5, hors entraînement et validation du reranker. Les attendus sont conservés séparément dans tests_s5/manifest_tests_s5.json ; ils ne doivent pas être transmis au modèle comme réponse à produire.

Le rapport décrit un état réel du corpus, pas une conformité complète à toutes les exigences du L1. Aucune donnée sensible réelle, aucun ticket de production et aucun résultat de performance du prototype ne sont introduits.



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

Fixer les versions et licences des outils ; mesurer mémoire et latence sur la RTX 3080 10 Go ; choisir l’OCR et la stratégie de découpage ; tester embeddings multilingues et recherche d’une preuve anglaise par une question française ; contrôler l’appui sémantique des citations et la reprise après attente d’approbation. L1 n’annonce aucune compatibilité mesurée.



## 4. Flux de données - Ingestion et métadonnées





Ingestion et métadonnées

### Étapes et contrôles

Étapes et contrôles

1. Vérifier présence du fichier, licence, provenance et validation humaine. Refuser un document absent de l’inventaire ou sans groupe d’accès.<br/>2. Conserver l’original et son empreinte ; détecter PDF texte ou PDF image.<br/>3. Extraire texte, tableaux et figures. L’OCR sera utilisé pour les scans qui restent à constituer ; les aperçus de pages ne sont pas comptés comme des scans sources.<br/>4. Découper en passages et éléments visuels, en conservant la page PDF physique et les renvois.<br/>5. Calculer les représentations textuelles et visuelles puis indexer avec les ACL héritées. Les fichiers de test restent identifiés.

| Métadonnée d’un élément | Exemple concret du corpus |

| document_id / version | dell_r720_manuel / Rev. A07 |

| page / element_id / type | 8 / figure_1 / figure |

| famille_equipement | serveurs_informatiques |

| equipement_ids | DELL_R720 ; DELL_R720XD |

| groupes_acces | techniciens_serveurs ; responsables |

| source_file | documents/serveurs/poweredge-r720_owners-manual_en-us.pdf |

| usage_test / provenance | normal / URL du PDF fabricant Dell |

| empreinte et extraction | SHA-256 du fichier ; OCR ou texte, avec confiance si disponible |

Une nouvelle version reçoit un identifiant ou une version distincte. Les deux versions fictives du dossier R720/R720xd sont conservées séparément : la v2 remplace la v1 au 01/11/2026. Une question sur une date antérieure doit retrouver la v1. Les PDF de test ne servent pas à l’entraînement.



## 4. Flux de données - Requête et contrôle d’accès





Requête et contrôle d’accès

### Parcours complet

Parcours complet

1. L’API authentifie l’utilisateur fictif et obtient ses groupes côté serveur.<br/>2. Le VLM décrit les indices visibles sans attribuer une cause non observée.<br/>3. Si l’équipement n’est pas établi, le workflow demande sa référence avant toute procédure spécifique.<br/>4. Les recherches textuelle et visuelle portent uniquement sur les documents autorisés ; les candidats sont fusionnés et reclassés.<br/>5. Un appel MCP utile consulte l’historique de l’équipement confirmé, après autorisation côté outil.<br/>6. Le VLM formule la réponse en français par défaut à partir des preuves françaises ou anglaises. Codes, références de pièces et unités restent inchangés. Le validateur contrôle la source originale, sa version, sa page et son appui.<br/>7. L’interface affiche la réponse, les limites et les sources ; leur ouverture déclenche un nouveau contrôle d’accès.

| Groupe | Périmètre autorisé |

| techniciens_fours | Les vingt notices RATIONAL attribuées à ce groupe et explicitement partagées avec responsables. |

| techniciens_serveurs | Les treize PDF Dell attribués à ce groupe ; pas les documents fours. |

| responsables | Deux familles explicitement partagées. La note de test est accessible au groupe fours pour qu’il puisse rencontrer l’injection ; l’accès aux documents serveurs reste interdit à ce groupe. |

| Groupe absent / inconnu | Refus par défaut ; aucune déduction de droits à partir d’un texte de document. |

### Illustration d’un refus

Illustration d’un refus

Un utilisateur techniciens_fours demande le manuel Dell R720 : la recherche ne lui renvoie ni extrait ni figure. Une requête directe vers le PDF ou son image extraite reste refusée. Le service MCP applique ses propres contrôles même si la recherche a déjà filtré le corpus.



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

| Erreur de métadonnées / données | 3 | 3 | Contrôler titres, chemins, séries, révisions et pages des PDF réels. | Ayoub |

| Droits de réutilisation / données | 3 | 3 | Conserver les copyrights ; ne pas publier les PDF ou leurs rendus sans autorisation. | Ayoub |

| Mémoire GPU insuffisante / technique | 2 | 3 | Mesurer tôt ; quantifier et prévoir un VLM plus petit. | Ayoub |

| OCR erroné / données | 2 | 2 | Comparer au PDF image, conserver positions et signaler l’incertitude. | Ayoub |

| Confusion modèle/version / données | 3 | 3 | Filtrer la configuration ; comparer versions ; demander le modèle. | Ayoub |

| Fuite entraînement/test / données | 2 | 3 | Séparer les documents avant génération des triplets du reranker. | Ayoub |

| Délai et relecture / organisation | 3 | 3 | Garder les 33 sources et trois tests ; traiter les exigences ouvertes et réserver la relecture finale. | Ayoub |

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

Définir en S5 les seuils et jeux de test. Mesurer nDCG@5 et MRR@10 pour le classement, appui documentaire et qualité des réponses françaises issues de sources anglaises. Tester aussi refus intergroupes, injections et absence de ticket non approuvé. Rapporter les résultats même si le fine-tuning n’améliore pas le classement.

Les scans sources restent à constituer. Les deux procédures contradictoires et la note piégée sont réservées au test S5 ; leur exécution n’a pas encore eu lieu. Les ambiguïtés de modèle seront testées avec des sources adéquates. Les images et textes tiers ne sont pas utilisés pour entraîner le modèle vision-langage, qui reste inchangé.



## 6. Planning et organisation - Remise, contrôles et limites déclarées





Remise, contrôles et limites déclarées

| Élément requis | Nom / état de préparation |

| Archive de travail locale | L1_MaintiDoc_BELOUANAS.zip - conformité L1 encore incomplète |

| Dossier racine | L1_MaintiDoc_BELOUANAS/ - quatre éléments seulement |

| Rapport | L1_MaintiDoc_BELOUANAS_Rapport.pdf - 14 pages prévues |

| Lien GitHub | L1_MaintiDoc_BELOUANAS_LienGitHub.txt - URL fournie par Ayoub |

| README | README.md - membre, objectif, contenu et structure |

| Corpus | L1_MaintiDoc_BELOUANAS_Corpus/ - 36 PDF, aperçus PNG, inventaire et scénarios S5 |

### Contrôles techniques réalisés

Contrôles techniques réalisés

Les contrôles portent sur la bijection entre les 36 PDF et l’inventaire, leurs noms exacts, pages, empreintes, séries, sources et liens vers les aperçus. Le contrôle technique n’efface pas les exigences encore ouvertes : scans sources, relecture et droits de redistribution des fabricants. Le journal détaillé est enregistré dans docs/controle_livraison.json. Ces contrôles ne remplacent pas la relecture humaine.

### Relecture et dépôt

Relecture et dépôt

1. Relire et corriger les documents puis compléter verifie_par et corrections. Les champs de relecture sont volontairement vides au moment de la préparation.<br/>2. Vérifier la version à remettre après cette relecture. Les métadonnées et liens sont publiés sur codex/livraison-l1. Les originaux fabricants restent locaux faute d’autorisation générale de redistribution établie. Les fichiers publiés ne constituent pas une validation humaine du corpus.

### Sources et audit

Sources et audit

Le journal liste les sources et contrôles effectués. Le paquet local de travail conserve les originaux pour vérification ; il ne constitue pas une autorisation de les redistribuer. Les archives synthétiques sont séparées du corpus actif. Les exigences non résolues sont explicites en partie 2.

Dépôt de l’équipe : <link href="https://github.com/ayoubbelouanas/maintidoc" color="#087E8B">github.com/ayoubbelouanas/maintidoc</link><br/>Référentiel pédagogique : L1, 29 octobre 2026, Mariam Cherrabi. Date de remise déclarée : 6 novembre 2026 ; aucune heure limite n’a été fournie.
