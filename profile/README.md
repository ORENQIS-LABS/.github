# CHARTE D'OPTIMISATION DE L'ORGANISATION ORENQIS-LABS

Ce document définit les standards obligatoires de l'organisation pour optimiser le contexte des IA (ChatGPT/Codex), structurer les projets et réduire l'empreinte de l'intégration continue (Green CI).

## 1. Structure de Documentation (Poupées Russes)
- **À la racine des dépôts :** Mettre systématiquement à jour le fichier `README.md` principal. Il doit servir de carte routière globale en explicitant l'architecture générale, la stack technique globale, et le rôle précis de chaque répertoire racine.
- **Dans les sous-dossiers techniques :** Installer un fichier `README.md` dédié au cœur de chaque composant ou technologie (ex: un dans le dossier Frontend Next.js, un dans le dossier Backend Python). Ce fichier doit lister les prérequis locaux, les commandes exactes de développement (npm, pip, pytest, docker) et les consignes de code strictes spécifiques au langage.

## 2. Étanchéité du Suivi Git (.gitignore)
Chaque dépôt doit maintenir un fichier `.gitignore` strict et mis à jour pour bloquer définitivement les fichiers caches et temporaires :
- **Écosystème Node / Frontend :** `.next/`, `node_modules/`, `dist/`, `.turbo/`, `playwright-report/`, `test-results/`
- **Écosystème Python / Backend :** `__pycache__/`, `.venv/`, `.pytest_cache/`, `.coverage`, `htmlcov/`
- **Écosystème iOS / Swift :** `DerivedData/`, `.build/`, `*.xcresult`, `.swiftpm`
- **Sécurité et Secrets :** Bloquer de manière étanche tous les fichiers d'environnement (`.env`, `.env.local`, `.env.*`). Seul un fichier `.env.example` contenant des variables documentées avec des valeurs fictives et sécurisées doit être suivi.

## 3. Optimisation Durable des Workflows (Green CI)
- Conserver la protection de la branche principale (`main`) et les checks de qualité requis obligatoires.
- Configurer les fichiers `.github/workflows/*.yml` avec des filtres de chemins intelligents (`paths`).
- **Règle de filtrage (Option 1) :** Le workflow global doit se déclencher pour valider les statuts requis par GitHub, mais les jobs internes lourds (tests complets, builds d'images) doivent être "sautés" (skipped) à l'aide de conditions si seules la documentation ou les chaînes de texte ont été modifiées.
