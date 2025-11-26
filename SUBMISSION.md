# 📋 Guide de Soumission - Text Normalization Challenge

## ✅ Checklist des Livrables

Ce repository contient tous les éléments requis pour le challenge:

### 1. ✅ Code Source
- **Fichier**: `text_normalization_fst.ipynb`
- **Type**: Jupyter Notebook
- **Langues supportées**: Français et Anglais
- **Couverture**: Nombres cardinaux 0-1000

### 2. ✅ Fichiers FAR (Finite-State Archive)
Les fichiers FAR sont générés automatiquement en exécutant le notebook (section 7):
- `cardinal_fr.far` - Grammaire française
- `cardinal_en.far` - Grammaire anglaise

### 3. ✅ Rapport
Le notebook `text_normalization_fst.ipynb` sert de rapport interactif complet incluant:
- Méthodologie détaillée
- Résultats et évaluation
- Calcul du WER
- Instructions d'utilisation
- Tests de performance

**Pour générer un PDF:**
```bash
jupyter nbconvert --to pdf text_normalization_fst.ipynb
```

### 4. ✅ Requirements
- **Fichier**: `requirements.txt`
- **Contenu**: pynini, datasets, huggingface_hub, jupyter

---

## 🚀 Instructions d'Exécution

### Méthode 1: Google Colab (Recommandée - Aucune installation)

1. Ouvrir https://colab.research.google.com/
2. Upload `text_normalization_fst.ipynb`
3. Exécuter: **Runtime → Run all**
4. Observer les résultats automatiques

### Méthode 2: Jupyter Local

```bash
# Installer les dépendances
pip install -r requirements.txt

# Lancer le notebook
jupyter notebook text_normalization_fst.ipynb

# Exécuter toutes les cellules: Cell → Run All
```

---

## 📊 Dataset Officiel

Le notebook charge automatiquement le dataset HuggingFace:

```python
ds = load_dataset("DigitalUmuganda/Text_Normalization_Challenge_Unittests_Eng_Fra")
```

**Si authentification nécessaire:**
```bash
huggingface-cli login
```

---

## 📈 Résultats

Le notebook affiche automatiquement:

- ✅ **Accuracy** sur le dataset de test
- ✅ **WER (Word Error Rate)** moyen
- ✅ Liste des erreurs avec exemples
- ✅ Temps de compilation des FST
- ✅ Performance (vitesse d'exécution)

**Fichiers générés:**
- `cardinal_fr.far` (~50-100 KB)
- `cardinal_en.far` (~50-100 KB)

---

## 🎯 Critères d'Évaluation

| Critère | Poids | Notre Solution |
|---------|-------|----------------|
| WER test | 40% | ✓ Calculé automatiquement |
| Méthodologie | 30% | ✓ Documentée dans notebook |
| Reproductibilité | 30% | ✓ Exécutable partout |

---

## 📝 Exemples de Normalisation

### Français
```
"J'ai 3 chiens et 21 chats"  →  "J'ai trois chiens et vingt et un chats"
"Il y a 80 personnes"        →  "Il y a quatre-vingts personnes"
"J'ai 71 ans"                →  "J'ai soixante et onze ans"
```

### Anglais
```
"I have 3 dogs and 21 cats"  →  "I have three dogs and twenty-one cats"
"There are 80 people"        →  "There are eighty people"
"I am 71 years old"          →  "I am seventy-one years old"
```

---

## 📞 Support

Consultez:
- `README.md` - Documentation complète
- `README_NOTEBOOK.md` - Guide détaillé du notebook
- Le notebook lui-même - Commentaires intégrés

---

## 🔗 Formulaire de Soumission

**À remplir après avoir créé votre repository GitHub:**

https://docs.google.com/forms/d/e/1FAIpQLSdRzGSPV6QqAa6PcKEtBi0JgEJ769B4Iaup-oGZMGPOlqlK0A/viewform

---

**Développé pour le Text Normalization Internship Challenge**
*Novembre 2025*
