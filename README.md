# VISIT - Assistant Intelligent de Planification de Voyages

> Projet développé par **Martial Bayom** | Formation Jedha Full Stack Data Science  
> Candidature stage - Audensiel Lab'Innov

---

##  Description

VISIT est un assistant touristique basé sur l'IA générative, capable de :
- **Comprendre la voix** de l'utilisateur (module ASR via Whisper)
- **Recommander des Points d'Intérêt** (embeddings sémantiques + LLM)
- **Afficher une carte interactive** des lieux recommandés
- **Évaluer ses propres performances** (WER, précision, latence)

---

##  Architecture

```
visit/
├── asr/
│   └── transcriber.py      # Module ASR (OpenAI Whisper)
├── poi/
│   └── generator.py        # Génération POI (embeddings + LLM)
├── api/
│   └── main.py             # Backend FastAPI
├── eval/
│   └── evaluator.py        # Évaluation WER, précision, latence
├── demo/
│   └── app.py              # Interface Streamlit
├── requirements.txt
└── .env.example
```

### Pipeline complet

```
Utilisateur
    │
    ▼ (voix ou texte)
[ASR — Whisper]
    │ texte transcrit
    ▼
[Embeddings — sentence-transformers]
    │ vecteur sémantique
    ▼
[ChromaDB — recherche vectorielle]
    │ POI pertinents
    ▼
[LLM — GPT / open-source]
    │ réponse naturelle enrichie
    ▼
[Streamlit — carte + réponse]
    │
    ▼
Utilisateur
```

---

##  Installation

### 1. Cloner le projet
```bash
git clone https://github.com/martial-bayom/visit.git
cd visit
```

### 2. Installer les dépendances
```bash
pip install -r requirements.txt
```

### 3. Configurer les variables d'environnement
```bash
cp .env.example .env
# Édite .env et ajoute ta clé OpenAI
```

---

## Lancement

### Démarrer l'API (Terminal 1)
```bash
python api/main.py
# API disponible sur http://localhost:8000
# Documentation : http://localhost:8000/docs
```

### Démarrer l'interface (Terminal 2)
```bash
streamlit run demo/app.py
# Interface disponible sur http://localhost:8501
```

### Lancer l'évaluation
```bash
python eval/evaluator.py
```

---

##  Stack technique

| Composant | Technologie |
|---|---|
| ASR | OpenAI Whisper |
| Embeddings | sentence-transformers (multilingual) |
| Base vectorielle | ChromaDB |
| LLM | GPT-3.5-turbo (OpenAI) |
| Backend API | FastAPI |
| Frontend | Streamlit |
| Carte | Folium |
| Conteneurisation | Docker |

---

##  Évaluation

| Métrique | Description | Objectif |
|---|---|---|
| WER | Word Error Rate (ASR) | < 10% |
| Precision@3 | Pertinence des 3 premiers POI | > 70% |
| Latence | Temps de réponse pipeline | < 2s |

---

##  Améliorations prévues

- [ ] Intégration OpenStreetMap pour des POI exhaustifs
- [ ] Support multilingue (EN, ES, DE)
- [ ] Historique conversationnel (mémoire entre sessions)
- [ ] Ranking contextuel avancé (heure, météo, profil utilisateur)
- [ ] Déploiement Docker + CI/CD

---

##  Auteur

**Martial Bayom**  
Formation : Jedha Full Stack Data Science  
Contact : martial.bayom@email.com
