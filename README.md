# MAINTiDOC

Projet du module Generative AI, EMSI. **Ayoub BELOUANAS**, travail individuel.
État au 6 novembre 2026. Architecture cible : prototype non encore implémenté.

## Structure du dépôt

```text
maintidoc/
├── README.md
├── .gitignore
├── docs/
│   └── diagrammes/
└── corpus/
    ├── inventaire.csv
    ├── prompts_corpus.md
    ├── documents/
    │   ├── fours/
    │   └── serveurs/
    └── images/
        ├── fours/
        └── serveurs/
```

Les quatre schémas sont dans [docs/diagrammes/](docs/diagrammes/).
L'[inventaire](corpus/inventaire.csv) décrit les 33 PDF du dépôt, avec leurs chemins exacts, sources, droits et usages de test. Le [journal des prompts](corpus/prompts_corpus.md) conserve les interventions de l'IA et l'historique des corrections.

## Corpus et disponibilité dans ce dépôt

Le dépôt comporte **33 PDF fabricants** :
- **fours** : 20 notices RATIONAL (iCombi Pro, iCombi Classic, SelfCookingCenter, iHexagon) ;
- **serveurs** : 13 PDF Dell PowerEdge/PERC 9.

Les 13 PDF Dell sont en anglais. Le système devra répondre en français par défaut, à partir de preuves françaises ou anglaises, et en anglais sur demande, en conservant les codes, unités et citations des pages originales.

**Les 33 PDF et les 25 aperçus PNG sont présents dans ce dépôt**, à la demande d'Ayoub, pour le projet pédagogique. Les PDF fabricants proviennent de publications publiques Dell et RATIONAL ; ils conservent leurs mentions de copyright. Leur disponibilité publique ne constitue pas une licence ouverte ; aucune permission générale de redistribution n'est revendiquée. Le champ `provenance` de l'inventaire indique les sources précises et les chemins correspondent aux fichiers publiés. Le [registre des images](corpus/images/tracabilite_images.csv) conserve la correspondance entre chaque aperçu, le PDF d'origine, sa page physique et ses empreintes. Les aperçus sont des pages illustrées, pas des photographies isolées.

## Accès prévu

- `techniciens_fours` : 20 PDF RATIONAL ;
- `techniciens_serveurs` : 13 PDF Dell ;
- `responsables` : les deux familles ; utilisateur inconnu : refus par défaut.

Contrôles prévus à l'API, avant la recherche, à l'ouverture des sources et côté MCP. Création de ticket après approbation humaine du contenu exact et contrôle d'idempotence.

## Tests réservés à la semaine 5

Les documents contradictoires seront complétés ultérieurement. Le document piégé et les scénarios de test restent également à préparer. Les futurs documents retenus seront signalés dans l'inventaire et exclus de l'entraînement et de la validation du reranker. Aucun test du prototype n'a démarré.

## État et limites

Le projet est actuellement en phase de conception. La plupart des tâches de réalisation n'ont pas encore démarré.
