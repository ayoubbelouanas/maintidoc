# MAINTiDOC

Je réalise **MAINTiDOC** dans le cadre du module Generative AI à l’EMSI.
**Ayoub BELOUANAS** - travail individuel.

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

J’ai retenu **33 PDF fabricants** :
- **fours** : 20 notices RATIONAL (iCombi Pro, iCombi Classic, SelfCookingCenter, iHexagon) ;
- **serveurs** : 13 PDF Dell PowerEdge/PERC 9.

Les 13 PDF Dell sont en anglais. Le système devra répondre en français par défaut, à partir de preuves françaises ou anglaises, et en anglais sur demande, en conservant les codes, unités et citations des pages originales.

J’ai conservé les noms et le contenu des 33 PDF d’origine. Les 25 PNG sont des aperçus de pages illustrées ; ce ne sont pas des photographies isolées. Le champ `provenance` de l’inventaire indique les sources précises. Le [registre des images](corpus/images/tracabilite_images.csv) relie chaque PNG au PDF source, à sa page physique et à ses empreintes.

## Licences et usage académique

J’utilise le corpus pour un projet académique non commercial, en conservant les documents et leurs mentions de copyright. Les [conditions Dell](https://www.dell.com/fr-fr/legal/lp/site-terms-of-use) permettent l’usage personnel non commercial sous réserve de préserver le contenu et les mentions de propriété. Les [mentions légales RATIONAL](https://portal.rational-online.com/fs4p/fr/footernavigation/impressum/impressum.php) exigent une autorisation expresse pour la reproduction dans d’autres publications. Je distingue l’usage pédagogique de la republication publique, sans assimiler ces documents à une licence ouverte.

## Authentification prévue

Je vais mettre en place une authentification obligatoire pour accéder à la plateforme, avec plusieurs types de comptes :

- **Technicien Dell** : accès aux documents et fonctions liés aux serveurs, groupe `techniciens_serveurs`.
- **Technicien RATIONAL** : accès aux documents et fonctions liés aux fours, groupe `techniciens_fours`.
- **Responsable maintenance** : accès aux deux familles, groupe `responsables`.

Je vérifierai les droits côté serveur avant chaque recherche, ouverture de source et appel MCP. Les rôles seront attribués au compte ; une question ou un document ne pourra pas modifier les permissions. L’authentification reste à développer.

## Accès documentaire prévu

- `techniciens_fours` : 20 PDF RATIONAL ;
- `techniciens_serveurs` : 13 PDF Dell ;
- `responsables` : les deux familles ; utilisateur inconnu : refus par défaut.

Contrôles prévus à l'API, avant la recherche, à l'ouverture des sources et côté MCP. Création de ticket après approbation humaine du contenu exact et contrôle d'idempotence.

## Tests réservés à la semaine 5

Je compléterai ultérieurement les documents contradictoires, le document piégé et les scénarios de test. Je signalerai les futurs documents dans l’inventaire et les réserverai aux tests, hors entraînement et validation du reranker. Les tests du prototype n’ont pas encore démarré.

## État et limites

Je suis actuellement en phase de conception. La plupart des tâches de réalisation n’ont pas encore démarré.
