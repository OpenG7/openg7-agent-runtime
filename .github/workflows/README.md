# Workflows du projet

agent-standards.yml vérifie le socle commun, les budgets et les références sans
installer d’application. Les manifests/workspaces du README sont encore des cibles.

Les workflows de dispatch claude-pr, codex-pr et gemini-pr nécessitent leur
configuration fournisseur. copilot-pr reste un placeholder gardé. Lire leur
configuration effective avant activation; aucune exécution externe n’est implicite.

ecosystem-guardrails utilise les contrôles locaux lorsqu’ils existent. Les
contrôles applicatifs viendront avec leurs implémentations. Les anciens workflows
copiés template-quality et sync-standards sont remplacés par le contrôle commun;
la synchronisation interprojets reste dans openg7-project-template.

Lire [AGENTS.md](../../AGENTS.md) et [la mission](../../README.md) pour le périmètre.
