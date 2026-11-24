# TP-Simulation-CICD

TP2 DevOps : Simulation d'un pipeline CI/CD avec GitHub Actions.

## Arborescence

TP-Simulation-CICD/
├── app.py
├── test_app.py
├── requirements.txt
└── .github/
    └── workflows/
        └── cicd.yml

## Étapes réalisées

1. Créer un dépôt GitHub nommé `TP-Simulation-CICD` (Public).
2. Préparer le projet Python avec l'arborescence ci-dessus.
3. Développer l'application (`app.py`) : `calculer_moyenne`, `mention`, `est_admis`.
4. Écrire les tests unitaires (`test_app.py`) avec Pytest.
5. Configurer le pipeline (`cicd.yml`) : Build & Test → Deploy Staging → Deploy Production.
6. Tester localement :

   ```bash
   python -m venv venv
   venv\Scripts\activate
   pip install -r requirements.txt
   pytest -v
   ```

7. Envoyer le projet sur GitHub :

   ```bash
   git init
   git add .
   git commit -m "Création application Python et pipeline CI-CD"
   git branch -M main
   git remote add origin https://github.com/VotreUser/TP-Simulation-CICD.git
   git push -u origin main
   ```

8. Observer l'exécution dans l'onglet Actions du dépôt (3 jobs : succès).
9. Simuler une erreur (changer le test attendu à `20`) → `Build and Test` échoue, `Deploy Staging` et `Deploy Production` sont ignorés (`Skipped`).
10. Corriger l'erreur et pousser à nouveau → les 3 jobs repassent en succès.

## Résultat attendu

- 4 tests passent localement et dans GitHub Actions.
- En cas d'échec des tests, les déploiements staging et production ne s'exécutent pas (grâce à `needs:`).
