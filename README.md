# F7 – Détection d'anomalies sur le S&P 500

**Auteur :** Ouhaddi Doha – Code Apogée 25007592 – Groupe 3 – S7 FIN
**Sujet :** F7, détection d'anomalies sur le S&P 500 (algorithme n° 24, Isolation Forest).
**Résumé :** on détecte les séances de bourse atypiques du S&P 500 avec un Isolation Forest ajusté sur le passé, et on le compare à la règle des trois écarts-types.

## Problématique et résultats
L'Isolation Forest repère-t-il mieux les séances de stress documentées que la règle |z| > 3 ?

Résultats sur la période de test (2026-08-10 → 2026-11-16, 70 séances) :

| Méthode | Jours signalés (%) | Événements retrouvés |
|---|---|---|
| Règle 3σ (référence) | 1,43 (1 jour sur 70) | 0 sur 0 |
| Isolation Forest | 2,86 (2 jours sur 70) | 0 sur 0 |

Les deux méthodes signalent la chute de −4,45 % du 5 novembre 2026 ; l'Isolation Forest ajoute le rebond de +2,32 % du 9 novembre. L'objectif chiffré n'est pas évaluable : les 11 événements documentés (2018–2025) sont hors de la période téléchargée (12 mois seulement). Voir `rapport/rapport.pdf`.

## Données
- Source : FRED, série SP500, https://fred.stlouisfed.org/series/SP500
- Extraction : 17/11/2026 (2025-11-17 → 2026-11-16, fréquence quotidienne)
- Licence : aucune mention dans le CSV ; voir les conditions d'utilisation sur la page FRED
- Obtention : fichier brut dans `data/raw/` ; sinon, téléchargement CSV depuis la page FRED (plage « Max »)
- Données préparées : `data/processed/sp500_variables.csv`

## Installation
Python 3.13 (Google Colab) :
`pip install -r requirements.txt`
(pandas 2.2.3, numpy 2.4.6, scikit-learn 1.6.1, matplotlib 3.10.0)

## Exécution
Ouvrir `notebooks/projet_F7.ipynb` (Google Colab ou Jupyter), puis « Redémarrer et tout exécuter ». Durée : quelques secondes. Le notebook télécharge les données depuis FRED et enregistre les graphiques dans `figures/`.

## Structure du dépôt
- `data/raw/`, `data/processed/` : données brutes et préparées
- `docs/` : fiche du sujet (`fiche_sujet_F7.md`) et `references.md`
- `notebooks/` : notebook final exécuté
- `figures/` : graphiques g1 à g5
- `rapport/` : `rapport.pdf` (export du notebook) et le rapport LaTeX
- `presentation/` : 6 diapositives (PDF et fichier source)
- `requirements.txt`, `.gitignore`, `DECLARATION_IA.md`

## Références
Voir `docs/references.md` et `DECLARATION_IA.md`.
