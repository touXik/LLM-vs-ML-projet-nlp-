# LLM vs ML — Projet NLP : Prédiction du Diabète

Comparaison de modèles de Machine Learning classiques et de grands modèles de langage (LLM) sur une tâche de classification médicale (diabète).

---

## Structure du projet
```
LLM-vs-ML-projet-nlp/
│
├── data/
│   ├── diabetes_dataset.csv      # Base de données principale
│   ├── train_ml.csv              # Données d'entraînement pour les modèles ML
│   ├── test_ml.csv               # Données de test pour les modèles ML
│   ├── test_zeroshot.csv         # Données de test pour les LLM en zero-shot
│   ├── train_finetune.csv        # Données d'entraînement pour le fine-tuning
│   └── test_finetune.csv         # Données de test pour le fine-tuning
│
├── pretraitement.ipynb           # Notebook de prétraitement des données
└── ML_vs_LLM.ipynb               # Notebook principal — entraînement & évaluation
```

---


## Étape 1 — Prétraitement des données (`pretraitement.ipynb`)

> Ce notebook génère tous les fichiers CSV du dossier `data/` à partir de la base de données principale.

### À faire avant d'exécuter :

1. Cloner ou télécharger ce dépôt.
2. S'assurer que le fichier `diabetes_dataset.csv` est bien placé dans le dossier `data/` :
```
LLM-vs-ML-projet-nlp/
└── data/
    └── diabetes_dataset.csv   ✅ obligatoire
```

3. Ouvrir `pretraitement.ipynb` avec Jupyter Notebook.
4. Exécuter toutes les cellules dans l'ordre (`Run All`).

### Résultat :

Les fichiers suivants seront générés et sauvegardés automatiquement dans `data/` :

- `train_ml.csv`
- `test_ml.csv`
- `test_zeroshot.csv`
- `train_finetune.csv`
- `test_finetune.csv`

---

## Étape 2 — Entraînement & Évaluation (`ML_vs_LLM.ipynb`)

> Ce notebook est conçu pour être exécuté sur **Google Colab**.  
> Il est divisé en **3 sections** indépendantes.

### 2.1 — Ouvrir le notebook sur Google Colab

1. Aller sur [https://colab.research.google.com](https://colab.research.google.com)
2. Importer le fichier `ML_vs_LLM.ipynb` depuis votre ordinateur ou depuis GitHub.

---

### Section 1 — Modèles Machine Learning

Les données sont importées **directement depuis GitHub** (aucun upload manuel nécessaire).

> ✅ Il suffit d'exécuter les cellules de cette section dans l'ordre.

Modèles entraînés et évalués :
- Logistic Regression
- Random Forest
- SVM
- Et d'autres...

Données utilisées : `train_ml.csv` et `test_ml.csv`

---

### Section 2 — LLM (Zero-Shot & Fine-Tuning)

#### 2a — Zero-Shot

Les données (`test_zeroshot.csv`) sont importées **directement depuis GitHub**.

Les modèles utilisés via API nécessitent des **clés secrètes**. Vous devez les configurer dans Colab **avant d'exécuter** les cellules correspondantes.

**Configurer les clés API dans Colab :**

1. Dans le menu Colab : `🔑 Secrets` (icône clé dans la barre latérale gauche)
2. Ajouter les secrets suivants :

| Nom du secret  | Valeur                        |
|----------------|-------------------------------|
| `MISTRAL_API_KEY` | Votre clé API Mistral      |
| `GROQ_API_KEY`    | Votre clé API Groq         |

3. Activer l'accès au notebook pour chaque secret.

---

#### 2b — Fine-Tuning

Les données de fine-tuning (`train_finetune.csv` et `test_finetune.csv`) doivent être **importées manuellement dans Colab** :

1. Dans Colab, cliquer sur l'icône 📁 (panneau de fichiers, barre latérale gauche)
2. Cliquer sur l'icône d'upload ⬆️
3. Importer les deux fichiers :
   - `train_finetune.csv`
   - `test_finetune.csv`
4. Ensuite exécuter les cellules de fine-tuning dans l'ordre.

> ⚠️ Les fichiers uploadés sur Colab sont temporaires. Si la session est réinitialisée, il faudra les réimporter.

---

## Résumé des sources de données par section

| Section              | Source des données                        |
|----------------------|-------------------------------------------|
| ML (entraînement)    | Import automatique depuis GitHub          |
| LLM Zero-Shot        | Import automatique depuis GitHub          |
| LLM Fine-Tuning      | Upload manuel dans Google Colab           |

---

## Notes importantes

- Ne pas modifier les noms des fichiers CSV ni leur emplacement dans `data/`.
- Le notebook `pretraitement.ipynb` doit être exécuté **avant** `ML_vs_LLM.ipynb` si les fichiers CSV ne sont pas déjà présents.
- Les clés API ne doivent **jamais** être écrites en clair dans le code. Utilisez toujours le gestionnaire de secrets de Colab.