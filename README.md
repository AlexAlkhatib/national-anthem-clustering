# 🌍 Anthem Clustering — NLP, TF-IDF & Unsupervised Learning

Analyse, vectorisation et clustering des hymnes nationaux pour regrouper les pays selon la similarité de leurs textes.


## 📌 Description du Projet

Ce projet consiste à analyser les hymnes nationaux du monde entier, nettoyer leur contenu textuel, puis appliquer plusieurs méthodes de **clustering non supervisé** afin d’identifier des regroupements sémantiques entre pays.

Le pipeline comprend :

* 🧼 Nettoyage linguistique (superficiel & sémantique)
* 🧠 Lemmatization + suppression des stopwords
* ✂️ Tokenisation + Vectorisation TF-IDF
* 🤖 Clustering K-Means & Hiérarchique
* 📊 Visualisation (PCA, carte du monde, dendrogrammes)
* ☁️ WordCloud des mots dominants par cluster

Ce projet met en évidence des compétences en **NLP, ML non supervisé, visualisation avancée et data storytelling**.


## 📂 Dataset

Dataset utilisé :
`anthems.csv` — hymnes nationaux + métadonnées pays

**Colonnes principales**

| Colonne           | Description              |
| ----------------- | ------------------------ |
| Country           | Nom du pays              |
| Anthem            | Texte de l’hymne         |
| Alpha-2 / Alpha-3 | Codes ISO                |
| Continent         | Continent d’appartenance |

---

## 🧹 Pipeline de Prétraitement

### ✔️ 1. Nettoyage Superficiel

* Mise en minuscules
* Suppression du HTML
* Suppression des caractères non alphabétiques
* Nettoyage des espaces

### ✔️ 2. Nettoyage Sémantique

* Tokenisation
* Lemmatization (`WordNetLemmatizer`)
* Suppression des stopwords (anglais)

### ✔️ 3. Vectorisation TF-IDF

* Création d’une matrice TF-IDF
* 3360 features générées
* Sauvegarde via pickle pour réutilisation


## 🤖 Clustering

### 🔷 K-Means

Application de K-Means avec recherche du **k optimal** via :

* Méthode du coude (Elbow)
* Méthode silhouette

📌 Résultat : `k ≈ 5` clusters optimaux

### 🔷 Clustering Hiérarchique

* Construction d’un dendrogramme (method=ward)
* Choix du nombre de clusters via :

  * Méthode du coude
  * Silhouette score

### 🔧 Ajout d’une colonne `cluster`

Le dataset final contient :

```
Country | Anthem | cluster | PCA1 | PCA2
```


## 📊 Visualisations

### ✔️ PCA (réduction à 2 dimensions)

Représentation des pays dans un espace 2D permettant de visualiser les clusters.

### ✔️ Carte du monde colorée

Chaque pays est affiché avec une couleur selon son cluster (via GeoPandas).

### ✔️ Nuages de mots (WordCloud)

WordCloud généré pour chaque cluster afin d’identifier :

* Les thèmes dominants
* Les valeurs récurrentes (liberté, patrie, paix…)
* Les différences culturelles entre continents

---

## 🗃️ Arborescence du Projet

```
📦 Anthem-Clustering
 ┣ 📄 anthems.csv
 ┣ 📄 anthems_vectorized.pkl
 ┣ 📄 anthems_with_clusters.csv
 ┣ 📄 notebook.ipynb
 ┣ 📄 README.md
```


## ▶️ Exécution du Projet

### 1. Installer les dépendances

```bash
pip install -r requirements.txt
```

### 2. Lancer l’analyse

```bash
python main.py
```

Ou ouvrir le notebook :

```bash
jupyter notebook anthem_clustering.ipynb
```


## 🚀 Technologies Utilisées

* Python 3.x
* pandas / numpy
* nltk
* scikit-learn
* matplotlib / seaborn
* TensorFlow Text (selon options)
* GeoPandas
* wordcloud


## ✨ Améliorations Futures

* Ajout d’un modèle Word2Vec / BERT pour une analyse sémantique plus profonde
* Classification supervisée des continents à partir des hymnes
* Détection automatique des thèmes (Topic Modeling – LDA)
* Web app interactive (Streamlit) pour explorer les clusters en direct


## 👤 Auteur

**Alex Alkhatib**
Projet NLP — Clustering des Hymnes Nationaux


## 📄 Licence
MIT License
Copyright (c) 2025 Alex Alkhatib
