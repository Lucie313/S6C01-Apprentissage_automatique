# S6C01-Apprentissage_automatique
**Lucie MASSELIN**
**Tsinjo RANDRIANARISON-RATSIANDAVANA**
**Flavien ALCAZAR**
**Aminata NGOM**

**Groupe :** Groupe 3

----

# SAE 6.1 : Analyse Intelligente des Avis Yelp

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

> **Attention :** Les fichiers de données étant volumineux, ils ne sont pas inclus dans ce dépôt. Veuillez les placer dans le dossier `data/raw/` après téléchargement.

---

## Méthodologie et Travail Réalisé

Le projet est divisé en trois phases distinctes :

### 1. Analyse Exploratoire de Données (EDA)
Analyse statistique approfondie pour comprendre le comportement des utilisateurs et des commerces :
* **Distribution :** Répartition des avis par catégories (Restaurants, Bars, etc.).
* **Corrélations :** Lien entre popularité d'un business et sévérité des notes.
* **Analyse Utilisateur :** Les "gros revieweurs" sont-ils plus sévères ?
* **Analyse Textuelle :** Comparaison de la longueur des avis et extraction des *Top 10 mots* (TF-IDF) par polarité.
* **Impact Photos :** Corrélation entre le nombre de photos et la note moyenne.

### 2. Modèles de Prédiction (ML & DL)
Nous avons comparé plusieurs approches pour deux tâches : 
* **Tâche 1 :** Classification de polarité (Négatif < 3, Neutre = 3, Positif > 3).
* **Tâche 2 :** Prédiction du score exact (1 à 5 étoiles).

**Matrice des expérimentations :**

| Représentation du Texte | ML Classique | Deep Learning (Keras/PyTorch) | Transformers (HuggingFace) |
| :--- | :--- | :--- | :--- |
| **Bag-of-Words** | Régression Logistique | MLP (Dense) | - |
| **TF-IDF** | SVM | - | - |
| **Embeddings** | - | CNN (Conv1D) | BERT / RoBERTa (Fine-tuning) |

### 3. IA Générative et Agentique (GenAI)
Utilisation de **LLM (Large Language Models)** via LangChain/LlamaIndex pour aller au-delà de la classification simple :
* **Zero-shot Classification :** Prédiction de polarité sans entraînement spécifique.
* **Aspect-Based Sentiment Analysis (ABSA) :** Extraction structurée des aspects spécifiques.
    * *Exemple de sortie :* `{ "Nourriture": "Positif", "Service": "Négatif", "Prix": "Neutre" }`.
* **Agentique :** Mise en place de chaînes de raisonnement pour l'analyse complexe.

---

## Installation et Utilisation

### Prérequis
* Python 3.10+
* Jupyter Notebook / Google Colab
* Compte pour API Key (OpenAI ou HuggingFace)

### Installation
1.  Cloner le dépôt :
    ```bash
    git clone [https://github.com/Lucie313/S6C01-Apprentissage_automatique.git](https://github.com/Lucie313/S6C01-Apprentissage_automatique.git)
    cd sae6-yelp-analysis
    ```
2.  Installer les dépendances :
    ```bash
    pip install -r requirements.txt
    ```
3.  Configuration des clés API (pour la partie GenAI) :
    Renommez `.env.example` en `.env` et ajoutez vos clés :
    ```
    OPENAI_API_KEY=sk-...
    ```

### Structure du Dépôt
```bash
├── data/              
├── notebooks/        
│   ├── 1_EDA_Analysis.ipynb
│   ├── 2_Classic_ML_Models.ipynb
│   ├── 3_Deep_Learning_BERT.ipynb
│   └── 4_GenAI_Agents.ipynb
├── src/               
├── results/           
├── requirements.txt  
└── README.md          

