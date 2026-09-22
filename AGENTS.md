# OpenG7 Agent Runtime — consignes

## Mission

Exécuter des tâches d’agents de façon contrôlée, observable et auditable.
Dépôt de cadrage : aucun workspace applicatif ni manifest racine actuellement.
Les APIs, dossiers et commandes du README sont des cibles à implémenter.

<!-- openg7:common:start -->

## Socle commun OpenG7

<!-- openg7-standard: 1 -->

- Respecter la mission du dépôt. Le code, les manifests et les tests décrivent
  l'existant; une architecture cible ou une roadmap ne prouve pas une livraison.
- Avant modification : `git status --short`, instructions des chemins concernés,
  code utile et équivalents existants. Préserver les changements de l'utilisateur.
- Lire uniquement les références déclenchées par le chemin ou le sujet traité,
  même pour un test ou un package. Chercher avec `rg`, lire la section utile;
  ne pas charger tout `docs/`, les registres ou les historiques par défaut.
- Réutiliser les contrats publics; éviter cycles, imports privés entre domaines,
  duplication métier et refactorisations étrangères à la demande.
- Ne placer aucun secret ni donnée privée inutile dans Git, sorties, logs, tests
  ou documentation. Exemples synthétiques; droits vérifiés côté serveur.
- Respecter l'autorisation déjà donnée et son périmètre. Préparer et vérifier les
  changements locaux autorisés; une demande de code n'autorise pas une opération
  de production, un envoi externe, une publication ou une destruction de données.
- Commit, push et ouverture de PR seulement dans le cadre demandé par l’utilisateur;
  une autorisation déjà donnée reste valable pour cette même opération et portée.
- Pour un effet externe : cible, droits, entrées/sorties, limites, idempotence,
  audit et reprise explicites. Réconcilier un résultat incertain avant de relancer.
- Choisir les validations selon le changement et les scripts réellement présents.
  Tester le comportement et les échecs pertinents; une modification documentaire
  seule ne déclenche pas les suites applicatives, les seeds ou un déploiement.
- Mettre à jour la référence propriétaire et les consommateurs d'un contrat dans
  le même changement. Les différences locales justifient une mission, une stack
  effective ou un risque métier; elles ne recopient pas le socle.
- Terminer par le diff, les contrôles applicables et `git diff --check`. Rapporter
  résultat, validations exécutées, limites et opérations restantes, sans faux succès.

<!-- openg7:common:end -->

## Périmètre local

Le runtime orchestre les outils et leurs états; les modèles passent par Model Gateway, les décisions d’accès par le moteur de politique et les connaissances par Knowledge Core. Il ne définit pas leurs règles métier.

- Outils structurés et autorisés : schémas entrée/sortie, permissions, environnement, délais, ressources, idempotence, audit, rédaction des champs sensibles et compensation.
- Sandbox jetable : réseau refusé par défaut, sorties autorisées explicitement, ressources bornées, aucun socket Docker hôte ni credential durable. Aucun shell de production libre.
- Persister transitions, checkpoints et leases; propager annulation et reprise. Aucun retry irréversible sans clé idempotente et état précédent vérifié.
- Les tâches critiques passent par la politique et une approbation humaine liée à l’action exacte. Le périmètre V1 vise analyse et préparation de patchs/PR, sans déploiement ni opération financière.
- La réussite exige des preuves de vérification; conserver les traces corrélées sans historique de prompts ou secrets inutile.

## Lectures selon la tâche

<!-- prettier-ignore -->
| Déclencheur | Référence |
| --- | --- |
| Frontière, nouveau module, dépendance | [Architecture](docs/ARCHITECTURE.md) |
| cycle de tâche, outils, sandbox, approbations, reprise et observabilité | Section correspondante du [README](README.md) |
| Révision des consignes | [Standard](docs/standards/README.md) |

## Validation

Documentation/gouvernance : `node scripts/check-project-standards.mjs` et
`git diff --check`. Pour du code, lire le manifest et la CI concernés; ne pas
annoncer un lint, test ou build absent comme exécuté.

## Maintenance

Pour changer les consignes : [standard et budgets](docs/standards/README.md).
Conserver le bloc commun synchronisé et les différences dans leur périmètre.
