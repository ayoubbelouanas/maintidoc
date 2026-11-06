# Vérification du rapport L1 - 6 novembre 2026

Revue des exigences fournies par Ayoub et des captures jointes. Ce contrôle porte sur la présence et la cohérence du contenu du rapport ; il n'atteste ni une implémentation ni une performance du prototype.

| Exigence | Emplacement dans le rapport final | Résultat de la revue |
|---|---|---|
| Schéma complet des blocs, flèches et données échangées | p.7 | Schéma vectoriel relié, 14 échanges numérotés et légende |
| Interface, API, orchestration, recherche, VLM, MCP, stockage | p.7-8 | Présents, avec ingestion et validation |
| Une fiche par bloc : rôle, entrées, sorties, outil envisagé | p.8 | Dix fiches en cinq colonnes |
| Droits d'accès sur le schéma | p.7 | C1 API, C2 recherche, C3 fichiers/images, C4 MCP |
| Validation humaine et vérification des citations sur le schéma | p.7 | C6 approbation ; C5 existence et appui des citations |
| Parcours pas à pas d'une question avec photo | p.10 | Exemple du voyant orange, sept étapes, clarification et ouverture protégée |
| Questions ouvertes et hypothèses | p.3 et p.8 | VRAM 10 Go, OCR conditionnel, découpage, recherche FR/EN, appui des citations |
| Flux d'ingestion, OCR, découpage, embeddings et métadonnées | p.9 | Original conservé, sélection OCR, passages et visuels, vecteurs et ACL |
| Flux de requête et contrôles d'accès | p.10 | Identité fiable, recherche autorisée, MCP, citations et ouverture |
| Flux de ticket : préparation, approbation, MCP, idempotence | p.11 | États, contenu exact, jeton, répétition et invalidation |
| Schéma des métadonnées d'un élément indexé | p.9 | Identifiant/version, page/élément, type d'équipement, groupes et provenance |
| Au moins deux groupes fictifs et répartition des documents | p.2 et p.10 | Fours : 21 PDF ; serveurs : 15 PDF ; responsables : les deux familles |
| Au moins huit risques avec catégorie, P/I, mesure, responsable | p.12 | Douze risques, six colonnes et échelles 1-3 |
| Risques minimaux, dont erreurs IA dans le corpus et licences | p.12 | Explicitement couverts avec hallucination/citations, fuite, ticket et matériel |
| Rôles par membre et planning S2-S6 | p.13 | Travail individuel d'Ayoub, fonctions et résultats par semaine |

Le rapport conserve 14 pages et les six sections dans l'ordre. La présence des rubriques ne lève pas les limites du livrable déclarées p.6 et p.14 : deux scans sources, relecture humaine et droits de réutilisation/remise restent à traiter.
