Projet 7 — Créez un tableau de bord dynamique avec Power BI (Sanitoral)




Contexte — Consultant Data Analyst chez ESN Data, vous êtes missionné chez Sanitoral (soins bucco‑dentaires) pour produire un reporting projet : suivi d’avancement, coûts, retards et performances. La mise à jour doit être hebdomadaire et automatisée via Power Query.

🧭 Résumé exécutif

Cadrage : Product Strategy Canvas (PSC) + user stories.

Prépa : ingestion, nettoyage et transformations Power Query (M), process de refresh documenté.

Modèle : schéma étoile (tables Faits / Dimensions), relations, rôles de sécurité (optionnel).

Viz : pages lisibles, KPI directeurs, alertes retards, drill‑down, filtres.

Storytelling : une page dédiée aux explications (PSC, étapes de mise à jour, modèle de données).

📦 Livrables

reports/Sanitoral_Projects.pbix — tableau de bord Power BI fonctionnel.

data/ — jeu(x) de données + dictionnaire fourni.

docs/ —

product_strategy_canvas.pdf (PSC validé)

data_update_procedure.md (procédure hebdomadaire de mise à jour)

data_model_explained.md (relations, cardinalités, clés)

accessibilite_checklist.md (bonnes pratiques)

exports/ — captures clés (.png) pour soutenance.

🔍 Données & préparation (Power Query)

Sources : extraits du logiciel de gestion de projets (2018–Début 2022) + dictionnaire.

Problèmes récurrents possibles :

Formats de dates hétérogènes, libellés incohérents, codes projets non uniques, codes pays/BU non normalisés.

Duplications de lignes, montants vides, retards non calculés (dates jalons manquantes).

Transformations (M) :

typage des colonnes ; split/merge ; unpivot ; mapping des statuts ; jointures Dim ;

colonnes calculées (dates de début/fin, retards, coûts réalisés, % avancement) ;

tables Dimension (Projets, Managers, BU/Région, Calendrier) & Fait (Suivi/Coûts/Retards).

🧱 Modèle de données (étoile)

Faits

F_Projets (id_projet, date, avancement_%, coût_reel, coût_prev, retard_jours, statut, …)

Dimensions

D_Projets (id_projet, nom, type, priorite, manager_id, bu_id, date_debut, date_fin_prev, date_fin_reelle, …)

D_Managers (manager_id, manager_nom)

D_BU (bu_id, bu_nom, region)

D_Calendrier (date, année, trimestre, mois, semaine)

Relations 1→* (Dimensions → Faits), direction de filtre single, éventuellement bidirectionnelle si besoin de symétrie contrôlée.

📊 Pages & visuels recommandés

Synthèse (Accueil)

KPIs : % projets on‑time, coût réel vs prévu, retard médian (jours), % en alerte.

Graphiques : barre statut, ligne retards dans le temps, carte BU/Région (si pertinent).

Détails Projets

Table projets avec barres de données ; filtres (BU, manager, statut, période).

Drill‑through vers fiche projet.

Alertes & Actions

Liste projets en retard (seuils paramétrables), coûts dérapés (> x%).

Segments pour isoler causes (ressource, fournisseur, BU… si disponibles).

PSC & Méthodo

PSC validé, process de mise à jour, modèle de données (diagramme + explications), liens vers le dictionnaire.

🔁 Mise à jour hebdomadaire (procédure)

Ouvrir Sanitoral_Projects.pbix.

Dans Power Query, cliquer Actualiser.

Vérifier la qualité (pas d’erreur, lignes attendues, statuts mappés).

Contrôler les mesures (écarts, retards) sur la période ajoutée.

Publier sur Power BI Service (si requis) ; planifier le refresh (gateway si sources locales).

♿ Accessibilité (rappels)

Contrastes suffisants, taille min. de police 12–14 px, légendes explicites.

Titres conclusifs (ex. « Retards en baisse de 12% au T4 »).

Alternatives textuelles / tooltips informatifs ; couleurs daltonisme‑friendly.

🎙️ Storytelling & soutenance

Règle 1 message par page ; fil narratif problème → analyse → action.

Mettre en avant un axe stratégique issu du reporting (ex. priorisation des BU à risque, re‑planification des jalons critiques).

📚 Ressources

Données Sanitoral + dictionnaire (fournis)

Vidéo : Initiez‑vous à l’art du storytelling – Prenez la parole en public (OpenClassrooms)

👤 Auteur & licence

Auteur : David Fernandes — David.Fernandes.data@gmail.com

Licence : CC BY‑NC‑SA 4.0
