# Text Normalization Challenge - Solution Jupyter Notebook

## 📓 Présentation

Cette solution implémente la normalisation de texte basée sur des **Transducteurs à États Finis (FST)** directement dans un **Jupyter Notebook** pour faciliter l'exploration, les tests et l'évaluation.

## 🚀 Démarrage Rapide

### Option 1: Google Colab (Recommandé)

1. Téléchargez `text_normalization_fst.ipynb`
2. Ouvrez-le dans Google Colab: https://colab.research.google.com/
3. Exécutez toutes les cellules (Runtime → Run all)

### Option 2: Jupyter Local

```bash
# Installer Jupyter
pip install jupyter notebook

# Lancer le notebook
jupyter notebook text_normalization_fst.ipynb
```

## 📋 Structure du Notebook

Le notebook contient 9 sections principales:

1. **Installation des dépendances** - `pynini`, `datasets`, `huggingface_hub`
2. **Implémentation du FST** - Classes `CardinalFST` et `TextNormalizer`
3. **Tests de base** - Validation française et anglaise
4. **Chargement du dataset HuggingFace** - Dataset officiel du challenge
5. **Calcul du WER** - Métrique Word Error Rate
6. **Évaluation sur le dataset** - Tests complets avec métriques
7. **Compilation FAR** - Export des fichiers `.far`
8. **Tests de performance** - Mesure de vitesse
9. **Résumé** - Conclusions et résultats

## 🎯 Utilisation du Dataset Officiel

### Dans le Notebook

Le notebook charge automatiquement le dataset officiel:

```python
from datasets import load_dataset

ds = load_dataset("DigitalUmuganda/Text_Normalization_Challenge_Unittests_Eng_Fra")
```

### Authentification (si nécessaire)

Si le dataset nécessite une authentification:

```python
from huggingface_hub import login
login()  # Entrez votre token HuggingFace
```

Ou via CLI avant de lancer le notebook:
```bash
huggingface-cli login
```

## 📊 Résultats Attendus

Après exécution complète du notebook, vous obtiendrez:

1. **Fichiers FAR compilés**:
   - `cardinal_fr.far` - Grammaire française
   - `cardinal_en.far` - Grammaire anglaise

2. **Métriques d'évaluation**:
   - Accuracy (%)
   - Word Error Rate (WER) moyen
   - Liste des erreurs avec exemples

3. **Performance**:
   - Temps de compilation
   - Vitesse d'exécution par phrase

## 🧪 Tests Inclus

### Tests Unitaires Intégrés

Le notebook teste automatiquement:
- Unités (0-9)
- Adolescents (10-19)
- Dizaines (20-99)
- Cas spéciaux français (70-79, 80-89, 90-99)
- Centaines (100-999)
- Mille (1000)
- Phrases complètes

### Exemples de Test

**Français:**
```python
"J'ai 3 chiens et 21 chats"
→ "J'ai trois chiens et vingt et un chats"

"Il y a 80 personnes"
→ "Il y a quatre-vingts personnes"
```

**Anglais:**
```python
"I have 3 dogs and 21 cats"
→ "I have three dogs and twenty-one cats"

"There are 80 people"
→ "There are eighty people"
```

## 📦 Fichiers Générés

Après exécution du notebook:

```
text_normalization_project/
├── text_normalization_fst.ipynb  # Notebook principal ✓
├── cardinal_fr.far                # FST français compilé ✓
├── cardinal_en.far                # FST anglais compilé ✓
└── ... autres fichiers
```

## 🔧 Dépannage

### Problème: Dataset ne se charge pas

**Solution 1**: Authentification
```python
from huggingface_hub import login
login()
```

**Solution 2**: Téléchargement manuel
```bash
git clone https://huggingface.co/datasets/DigitalUmuganda/Text_Normalization_Challenge_Unittests_Eng_Fra
```

**Solution 3**: Utiliser des fichiers de test locaux
```python
# Créer votre propre liste de tests
test_data = [
    {"input": "J'ai 3 chiens", "output": "J'ai trois chiens"},
    # ... plus de tests
]
```

### Problème: Pynini ne s'installe pas

**Sur Google Colab**: Normalement pré-installé

**Sur système local**:
```bash
# Ubuntu/Debian
sudo apt-get install libfst-dev
pip install pynini

# MacOS
brew install openfst
pip install pynini

# Windows
# Utiliser WSL ou Docker
```

## 💡 Avantages du Format Notebook

1. **Interactif**: Exécution cellule par cellule
2. **Visualisation**: Résultats immédiats
3. **Itératif**: Modification et test rapides
4. **Documenté**: Explications intégrées
5. **Partageable**: Compatible Google Colab

## 📝 Adaptation du Code

### Modifier la langue

```python
# Créer un normaliseur
normalizer = TextNormalizer(language='fr')  # ou 'en'

# Normaliser du texte
result = normalizer.normalize_text("J'ai 21 chats")
```

### Ajouter de nouveaux tests

```python
# Dans la section 3 du notebook
my_tests = [
    "Ma phrase avec 42 nombres",
    "Un autre test avec 99 exemples"
]

for test in my_tests:
    print(normalizer.normalize_text(test))
```

### Exporter les résultats

```python
# Sauvegarder les résultats dans un fichier
import json

with open('results.json', 'w') as f:
    json.dump(results_fr, f, indent=2, ensure_ascii=False)
```

## 🎓 Pour le Challenge

### Checklist de Soumission

- ✅ Notebook exécutable (`text_normalization_fst.ipynb`)
- ✅ Fichiers FAR générés (`cardinal_fr.far`, `cardinal_en.far`)
- ✅ Tests sur dataset officiel
- ✅ Calcul du WER
- ✅ Documentation complète

### Exportation

Le notebook peut être converti en:

1. **HTML** (pour visualisation):
```bash
jupyter nbconvert --to html text_normalization_fst.ipynb
```

2. **PDF** (pour le rapport):
```bash
jupyter nbconvert --to pdf text_normalization_fst.ipynb
```

3. **Python script**:
```bash
jupyter nbconvert --to python text_normalization_fst.ipynb
```

## 🔗 Ressources

- **Pynini Documentation**: https://www.openfst.org/twiki/bin/view/FST/WebHome
- **HuggingFace Datasets**: https://huggingface.co/docs/datasets/
- **Google Colab**: https://colab.research.google.com/

## 📧 Support

Pour toute question sur le notebook:
1. Vérifiez les commentaires dans le code
2. Consultez la section "Dépannage" ci-dessus
3. Examinez les résultats des cellules de test

---

**Bonne chance pour le challenge ! 🚀**
