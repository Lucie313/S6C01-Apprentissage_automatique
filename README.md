# S6C01-Apprentissage_automatique
- **Lucie MASSELIN**
- **Tsinjo Mirantsoa RANDRIANARISON RATSIANDAVANA**
- **Flavien ALCAZAR**
- **Aminata Oumou Rassoul NGOM**

**Groupe :** Groupe 3

----

**Matière :** SAE -S6.C01 : Apprentissage automatique 
**Date Début :** 26 Janvier 2026  
**Support :** [Yelp Open Dataset](https://www.yelp.com/dataset)

---

## Contexte du Projet

Dans un contexte où les avis en ligne (Yelp, TripAdvisor) dictent les choix des consommateurs, la capacité à analyser automatiquement des millions de commentaires est cruciale. 

Ce projet a pour objectif de concevoir une pipeline complète d'analyse de données et d'intelligence artificielle capable de :
1. Comprendre la répartition et les biais des données Yelp.
2. Prédire la note et la polarité d'un avis via des modèles de **Machine Learning** et **Deep Learning**.
3. Extraire des informations fines (aspects positifs/négatifs) en utilisant l'**IA Générative et Agentique**.

---

## Le Dataset

Le projet s'appuie sur le **Yelp Open Dataset**, un jeu de données riche comprenant :
* `review.json` : Texte des avis et notes (1-5 étoiles).
* `business.json` : Métadonnées des commerces (catégorie, localisation).
* `user.json` : Profils des utilisateurs (influence, ancienneté).
* `photo.json` : Métadonnées des images associées.

> **Attention :** Les fichiers de données étant volumineux, ils ne sont pas inclus dans ce dépôt.

---

## Méthodologie et Travail Réalisé

Le projet est divisé en trois phases distinctes :

### 1. Analyse Exploratoire de Données (EDA)
Analyse statistique approfondie pour comprendre le comportement des utilisateurs et des commerces :
* **Distribution :** Répartition des avis par catégories (Restaurants, Bars, etc.).
* **Corrélations :** Lien entre popularité d'un business et sévérité des notes.
* **Analyse Utilisateur :** Les "gros revieweurs" sont-ils plus sévères ?
* **Analyse Textuelle :** Comparaison de la longueur des avis et extraction des *Top 10 mots* (TF-IDF) par polarité.
* **Impact Photos :** Corrélation entre le nombre de photos et la note moyenne. (que nous n'avons pas pu faire car pas de données)

### 2. Modèles de Prédiction
Nous avons comparé plusieurs approches pour deux tâches : 
* **Tâche 1 :** Classification de polarité (Négatif < 3, Neutre = 3, Positif > 3).
* **Tâche 2 :** Prédiction du score exact (1 à 5 étoiles).

**Matrice des expérimentations :**

| Représentation du Texte | Machine Learning | Deep Learning | IA Générative |
| :--- | :--- | :--- | :--- |
| **Bag-of-Words** | Testé (Baseline) | Testé | - |
| **TF-IDF** | SVM / Reg. Log. | MLP / CNN / BERT / LSTM | - |
| **BM25** | Testé | Testé | - |
| **Fine-tuning** | - | - | DistilBERT / RoBERTa |
| **Zero/Few-shot** | - | - | Flan-T5 |

### 3. IA Générative et Agentique (GenAI)
Exploration des modèles **Text-to-Text** pour aller au-delà de la classification simple.

* **Zero-shot & Few-shot Learning** : Utilisation de **Google Flan-T5-Base** pour classer les avis sans (ou avec très peu) d'exemples d'entraînement, grâce au *Prompt Engineering*.
* **Aspect-Based Sentiment Analysis (ABSA)** : Extraction automatique d'opinions par thèmes (Nourriture, Service, Prix) avec une sortie structurée au format **JSON**.
* **Framework Agentique** : Mise en œuvre de **LangChain** pour créer des chaînes de raisonnement (*Chain of Thought*), améliorant la fiabilité des analyses complexes.

---

## Installation et Utilisation

### Prérequis
* Python 3.12.10
* Jupyter Notebook / Google Colab

### Installation
Cloner le dépôt :
```bash
git clone [https://github.com/Lucie313/S6C01-Apprentissage_automatique.git](https://github.com/Lucie313/S6C01-Apprentissage_automatique.git)
cd sae6-yelp-analysis
```
