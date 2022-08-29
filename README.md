# demo-ci

# Pipeline
name: learn-github-action # Nom du workflow
on: [push]
jobs:
  # Premier job
  check-bats-version:
    # Définition du runner (ubuntu:latest)
    runs-on: ubuntu-latest
    # Déclaration de la liste des steps
    steps:
      # Action par défaut qui permet de récupérer le code de répo
      - uses: actions/checkout@v3
      # Action qui permet d'installer node
      - uses: actions/setup-node@v3
        # with permet de passer des arguments
        with:
          # Indication de l'installation de la version 14
          node-version: '14'
      # Run permet d'executer une commande bash
      - run: npm install -g bats
      - run: bats -v
