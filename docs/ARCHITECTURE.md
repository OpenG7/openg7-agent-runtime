# OpenG7 Agent Runtime — architecture

## Mission et état

Exécuter des tâches d’agents de façon contrôlée, observable et auditable.
Le dépôt contient actuellement cadrage et gouvernance. Les modules décrits
dans le [README](../README.md) sont une architecture cible, pas du code livré.
Aucun build applicatif n’est disponible avant ajout de ses manifests et sources.

## Frontières

Le runtime orchestre les outils et leurs états; les modèles passent par Model Gateway, les décisions d’accès par le moteur de politique et les connaissances par Knowledge Core. Il ne définit pas leurs règles métier.

Transport API et workers → orchestration durable → domaine et ports → adaptateurs d’outils, sandbox, stockage et services externes. Les états et contrats restent indépendants du fournisseur de modèle.

## Invariants de conception

Appliquer les [invariants du projet](../AGENTS.md#périmètre-local) aux contrats,
aux adaptateurs et à leurs tests; ils restent définis à cet endroit unique.

## Évolution

Garder les contrats de domaine indépendants des fournisseurs et les effets dans
les adaptateurs. Pour matérialiser un module, documenter ses entrées/sorties,
consommateurs, permissions, état d’implémentation et validations disponibles.
Mettre à jour cette frontière si elle change; les consignes d’exécution restent
dans [AGENTS.md](../AGENTS.md), sans recopier une autre stack.
