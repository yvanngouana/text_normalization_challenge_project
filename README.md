# Text Normalization using Finite-State Transducers (FST)

## Challenge de Stage - Normalisation de Texte

Ce projet implémente un système de normalisation de texte basé sur des **Transducteurs à États Finis (FST)** pour convertir les nombres cardinaux (0-1000) en leur forme écrite, en français et en anglais.

## 🎯 Objectif

Normaliser les nombres cardinaux dans des phrases:
- **Input**: `J'ai 3 chiens et 21 chats`
- **Output**: `J'ai trois chiens et vingt et un chats`

## 📦 Livrables

Ce dépôt contient tous les éléments requis pour le challenge:

1. ✅ **Code source**: `text_normalization_fst.ipynb` - Notebook Jupyter complet
2. ✅ **Fichiers FAR**: Générés par le notebook
   - `cardinal_fr.far` - Grammaire française
   - `cardinal_en.far` - Grammaire anglaise
3. ✅ **Documentation**: Ce README + documentation dans le notebook
4. ✅ **Requirements**: `requirements.txt`

## 🚀 Démarrage Rapide

### Option 1: Google Colab (Recommandé - Aucune installation nécessaire)

1. Téléchargez `text_normalization_fst.ipynb`
2. Ouvrez https://colab.research.google.com/
3. Uploadez le notebook
4. Exécutez toutes les cellules: **Runtime → Run all**

### Option 2: Jupyter Local

```bash
# Cloner le repository
git clone <votre-repo-url>
cd text_normalization_project

# Installer les dépendances
pip install -r requirements.txt

# Lancer Jupyter
jupyter notebook text_normalization_fst.ipynb
```

## 📊 Utilisation du Dataset Officiel

Le notebook charge automatiquement le dataset HuggingFace:

```python
from datasets import load_dataset
ds = load_dataset("DigitalUmuganda/Text_Normalization_Challenge_Unittests_Eng_Fra")
```

### Authentification (si nécessaire)

```bash
# Via CLI
huggingface-cli login

# Ou dans le notebook
from huggingface_hub import login
login()
```

## 🧪 Ce qui est Testé

Le système normalise correctement:

### Français
- ✅ Unités (0-9): `3` → `trois`
- ✅ Adolescents (10-19): `15` → `quinze`
- ✅ Dizaines (20-69): `21` → `vingt et un`
- ✅ Cas spéciaux:
  - 70-79: `71` → `soixante et onze`
  - 80: `80` → `quatre-vingts`
  - 81-89: `81` → `quatre-vingt-un`
  - 90-99: `91` → `quatre-vingt-onze`
- ✅ Centaines:
  - `100` → `cent`
  - `200` → `deux cents`
  - `201` → `deux cent un`
- ✅ Mille: `1000` → `mille`

### Anglais
- ✅ Unités (0-9): `3` → `three`
- ✅ Adolescents (10-19): `15` → `fifteen`
- ✅ Dizaines (20-99): `21` → `twenty-one`
- ✅ Centaines: `235` → `two hundred thirty-five`
- ✅ Mille: `1000` → `one thousand`

## 🎓 Structure du Notebook

Le notebook `text_normalization_fst.ipynb` contient 9 sections:

1. **Installation** - Dépendances (`pynini`, `datasets`)
2. **Implémentation FST** - Classes principales
3. **Tests de base** - Validation rapide
4. **Dataset HuggingFace** - Chargement du dataset officiel
5. **Calcul WER** - Métrique Word Error Rate
6. **Évaluation** - Tests complets avec métriques
7. **Compilation FAR** - Export des grammaires
8. **Performance** - Mesure de vitesse
9. **Résumé** - Conclusions et résultats

## 📈 Résultats Attendus

Après exécution du notebook:

- **Fichiers FAR**: `cardinal_fr.far`, `cardinal_en.far`
- **Métriques**:
  - Accuracy sur le dataset officiel
  - WER (Word Error Rate)
  - Liste des erreurs avec exemples
- **Performance**:
  - Temps de compilation: < 1 seconde
  - Vitesse d'exécution: < 1ms par phrase

## 🛠️ Fonctionnalités Clés

### Implémentation FST Complète

```python
# Dans le notebook
class CardinalFST:
    \"\"\"Construit des transducteurs à états finis pour 0-1000\"\"\"

class TextNormalizer:
    \"\"\"Applique le FST aux phrases complètes\"\"\"
```

### Utilisation Simple

```python
from fst_cardinal import TextNormalizer

# Créer le normaliseur
normalizer = TextNormalizer(language='fr')

# Normaliser
result = normalizer.normalize_text("J'ai 21 chats")
print(result)  # "J'ai vingt et un chats"
```

## 📝 Export du Notebook

Le notebook peut être converti en différents formats:

```bash
# HTML (pour visualisation)
jupyter nbconvert --to html text_normalization_fst.ipynb

# PDF (pour rapport)
jupyter nbconvert --to pdf text_normalization_fst.ipynb

# Python script
jupyter nbconvert --to python text_normalization_fst.ipynb
```

## 🔧 Dépannage

### Pynini ne s'installe pas

**Google Colab**: Normalement pré-installé

**Local Ubuntu/Debian**:
```bash
sudo apt-get install libfst-dev
pip install pynini
```

**Local MacOS**:
```bash
brew install openfst
pip install pynini
```

### Dataset ne se charge pas

1. Authentifiez-vous: `huggingface-cli login`
2. Vérifiez votre connexion internet
3. Utilisez des fichiers de test locaux si nécessaire

## 📚 Références

1. **E. Roche and Y. Schabes (eds.)**, *Finite-State Language Processing*. MIT Press, 1997.
2. **Pynini Documentation**: https://www.openfst.org/twiki/bin/view/FST/WebHome
3. **HuggingFace Datasets**: https://huggingface.co/docs/datasets/

## 🎯 Critères d'Évaluation

| Critère | Poids | Notre Approche |
|---------|-------|----------------|
| WER sur test | 40% | ✓ Calculé automatiquement dans le notebook |
| Méthodologie | 30% | ✓ Documentation complète + explications |
| Reproductibilité | 30% | ✓ Notebook exécutable + requirements.txt |

## 👤 Auteur

Développé pour le **Text Normalization Internship Challenge**

## 📄 License

Ce projet est soumis dans le cadre d'un challenge de stage.

---

## 🚀 Pour Commencer Maintenant

1. **Ouvrir le notebook**: `text_normalization_fst.ipynb`
2. **Exécuter toutes les cellules**
3. **Observer les résultats** et métriques
4. **Télécharger les fichiers FAR** générés

**C'est tout ! Le notebook fait tout automatiquement. 🎉**
