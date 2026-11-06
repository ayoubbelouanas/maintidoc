# Plan du corpus - état réel

Le corpus actif est dans corpus_reel_candidats/ ; une copie synchronisée est dans L1_MaintiDoc_BELOUANAS_corpus/. Les noms d’origine des PDF sont conservés. L’ancien lot synthétique est dans archives/corpus_synthetique_remplace_2026_11_06/.

Le lot comporte 33 PDF fabricants, auxquels s’ajoutent trois PDF synthétiques de test S5 : 20 notices RATIONAL, dix manuels propriétaires Dell, deux guides techniques Dell et un guide PERC 9. iDRAC et Lifecycle Controller ne sont pas présents. L’inventaire UTF-8 comprend vingt colonnes et une ligne par PDF. Les 25 aperçus de pages sont des ressources liées et ne changent pas le nombre de documents.

Reste à traiter pour le L1 : relecture humaine, conditions de réutilisation du lot et deux scans sources pour OCR. Les deux versions contradictoires et la note d’injection sont préparées. Ces exigences ne sont pas déclarées satisfaites par l’ancienne version synthétique rejetée.

Voir etat_corpus_reel.md, corpus_actuel.json et l’inventaire pour les séries, les versions et les chemins réellement présents.


## Politique linguistique

Les 13 PDF Dell sont en anglais (langue = en). Les réponses seront en français par défaut, avec explication ou traduction à partir des preuves anglaises et citations vers les pages originales ; codes, références et unités sont conservés. Voir politique_langues.md. Validation bilingue prévue pendant les tests.


## Ajout autorisé P14 - tests S5

Total actif : 36 PDF = 33 publications fabricants inchangées + trois PDF synthétiques de test. `dell_revue_dossier_v1` et `dell_revue_dossier_v2` sont signalés contradictoire ; `rational_note_suivi_injection_s5` est signalé injection. Les trois sont exclus de l’entraînement et de la validation. Voir tests_s5.md et le manifeste du corpus ; aucun résultat d’exécution n’est déclaré.
