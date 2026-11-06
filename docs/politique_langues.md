# Langues des sources et des réponses

## Corpus réellement présent

Les 13 PDF Dell sont en anglais : le champ langue vaut en dans leurs treize lignes d’inventaire. Les 20 notices RATIONAL sont décrites avec le français comme langue principale ; MI_2208 est multilingue et sa section française commence p.17. Les PDF sources restent dans leur langue d’origine. Les trois procédures synthétiques de test S5 sont en français ; le total du corpus est donc de 23 documents en français principal et 13 en anglais.

## Comportement retenu pour le prototype

La réponse est rédigée en français par défaut, même si les preuves récupérées sont en anglais. Si l’utilisateur demande explicitement une réponse en anglais, cette préférence est respectée. La langue du document et la langue de la réponse sont deux paramètres distincts.

Une question française doit pouvoir retrouver un passage anglais : embeddings et reranking multilingues seront testés pour cette recherche interlingue. À partir du passage anglais, le modèle reformule la réponse utile en français ; il n’est pas nécessaire de traduire préalablement l’ensemble des PDF ni de remplacer les originaux.

Conserver à l’identique les codes d’erreur, messages affichés, références de pièces, noms de modèles, unités et valeurs numériques. Un message anglais peut être reproduit brièvement tel quel avec une explication française. Si un terme technique est ambigu, conserver le terme anglais entre parenthèses plutôt que lui attribuer un sens non établi.

Les citations pointent vers le document anglais original et sa page réelle. Une traduction explicative est présentée comme telle ; elle n’est pas une citation française supposément présente dans la source.

## Vérification prévue, pas encore exécutée

| Cas de test | Résultat attendu |
|---|---|
| Question française, preuve dans un PDF Dell anglais | Réponse française fondée sur le passage anglais, avec citation du PDF original |
| Code ou référence de pièce dans la source | Chaîne, valeur et unité conservées sans traduction ni correction silencieuse |
| Demande explicite de réponse en anglais | Réponse en anglais avec les mêmes sources |
| Terme ou passage insuffisamment compris | Incertitude signalée, terme original conservé et précision demandée |

Il s’agit du comportement cible du prototype. La qualité de recherche et de traduction sera évaluée ; aucune performance bilingue n’est déclarée déjà mesurée.
