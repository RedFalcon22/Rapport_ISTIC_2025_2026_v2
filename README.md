# Rapport PFE — Intégration d'agents intelligents dans une plateforme de détection du cyberharcèlement

**ISTIC 2025–2026 | Smart-Conseil — Netethic**

---

## Prérequis

### Installer MiKTeX (Windows)

1. Télécharge l'installeur sur **[miktex.org/download](https://miktex.org/download)**
2. Lance `basic-miktex-*.exe` et suis l'assistant
3. Lors de l'installation, choisis :
   - **Install missing packages on-the-fly** → `Yes`
   - **Paper size** → `A4`
4. Une fois installé, ouvre **MiKTeX Console** et clique sur **Check for updates** puis **Update now**
5. Vérifie l'installation en ouvrant PowerShell :
   ```powershell
   pdflatex --version
   bibtex --version
   ```
   Tu dois voir les numéros de version s'afficher.

> **macOS / Linux :** installe [TeX Live](https://tug.org/texlive/) à la place de MiKTeX. Les commandes de compilation restent identiques.

---

## Cloner le projet

```bash
git clone https://github.com/RedFalcon22/Rapport_ISTIC_2025_2026_v2.git
cd Rapport_ISTIC_2025_2026_v2
```

---

## Compiler le rapport

Ouvre un terminal (PowerShell ou CMD) dans le dossier du projet et exécute les 4 commandes dans l'ordre :

```powershell
pdflatex Main.tex
bibtex Main
pdflatex Main.tex
pdflatex Main.tex
```

Le fichier **`Main.pdf`** est généré dans le même dossier.

> **Pourquoi 4 commandes ?**
> - `pdflatex Main.tex` (1ère passe) — compile le document et détecte les références manquantes
> - `bibtex Main` — résout la bibliographie (`Biblio.bib`)
> - `pdflatex Main.tex` (2ème passe) — intègre la bibliographie
> - `pdflatex Main.tex` (3ème passe) — stabilise les numéros de figures, tables et références croisées

---

## Structure du projet

```
Rapport_ISTIC_2025_2026_v2/
├── Main.tex                  # Fichier principal (point d'entrée)
├── Biblio.bib                # Bibliographie
├── Introduction.tex
├── Chapitre1.tex             # Cadre du projet
├── chapitre2.tex             # Spécification des besoins
├── Chapitre3.tex             # État de l'art et choix technologiques
├── Chapitre4.tex             # Conception (diagrammes UML)
├── Chapitre5.tex             # Réalisation et tests
├── Conclusion.tex
├── figures/                  # Sources PlantUML (.puml)
├── figures_png/              # Diagrammes UML exportés (.png)
└── *.png / *.jpg             # Images et logos
```

---

## Workflow Git (collaboration)

**Récupérer les dernières modifications :**
```bash
git pull
```

**Envoyer tes modifications :**
```bash
git add .
git commit -m "description de tes changements"
git push
```

**En cas de conflit :** résous les conflits dans le fichier concerné, puis :
```bash
git add fichier_modifie.tex
git commit -m "résolution conflit"
git push
```
