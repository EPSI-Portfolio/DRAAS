# DRAAS — Disaster Recovery as a Service

> Vos données, toujours en sécurité.

DRAAS est une solution de continuité d’activité abordable et automatisée, destinée aux petites et moyennes entreprises (PME) qui n’ont généralement ni sauvegardes ni plan de reprise ou de continuité d’activité (PRA/PCA). Elle ne nécessite aucune expertise technique poussée.

**Ce qui nous distingue :**
- Des prix accessibles
- Une interface simple et moderne
- Des tests de reprise automatiques et réguliers
- Des rapports de conformité

---

## Fonctionnement

1. L’**agent de sauvegarde** est installé sur les machines du client. Il collecte les fichiers et envoie les sauvegardes.
2. Le **backend** (FastAPI) orchestre et coordonne les sauvegardes et les restaurations. Il ne stocke pas les fichiers lui-même.
3. **MinIO** stocke les fichiers de sauvegarde (stockage objet compatible S3).
4. **PostgreSQL** stocke les métadonnées (clients, machines, historique des sauvegardes, planifications).
5. Le **frontend** affiche l’ensemble : tableau de bord, état des sauvegardes, restauration et rapports.

---

## Stack technique

| Partie | Technologies |
|---|---|
| Frontend | React, TypeScript, Tailwind CSS, Vite, React Router |
| Backend | Python, FastAPI, PostgreSQL, Redis |
| Agent de sauvegarde | Python |
| Stockage | MinIO |
| Infrastructure | Docker, Docker Compose |
| Supervision | Prometheus, Grafana, Alertmanager |
| Journaux | ELK Stack ou Loki |
| Sécurité | Vault (gestion des secrets), fail2ban, pare-feu applicatif web (WAF) |

---

## Structure du dépôt

```
DRAAS/
├── frontend/   Interface web (React)
├── backend/    API et orchestration (FastAPI)
├── agent/      Agent de sauvegarde installé chez le client (Python)
├── infra/      Déploiement, Docker, supervision, configuration réseau et sécurité
└── docs/       Cahier des charges, schémas et documentation du projet
```

---

## Démarrage

> Le projet en est à ses débuts. Ces étapes seront complétées au fur et à mesure du développement.

**Prérequis :** Git, Docker et Docker Compose, Python 3.11 ou plus récent, Node.js 20 ou plus récent.

```
git clone https://github.com/EPSI-Portfolio/DRAAS.git
cd DRAAS
```

Les instructions d’installation de chaque partie se trouveront dans son propre README.

---

## Équipe

| Rôle | Périmètre |
|---|---|
| Charlotte | Agent de sauvegarde et backend |
| Akram     | Frontend et pages de restauration |
| Paul      | À compléter |
| Erwann    | À compléter |

---

## Règles de travail

- Ne jamais pousser directement sur `main`. Créer une branche par fonctionnalité, par exemple `feature/agent-upload` ou `fix/login-error`.
- Fusionner via une pull request, relue par au moins un autre membre de l’équipe.
- Écrire des messages de commit clairs qui décrivent le changement, par exemple `Ajout de l’envoi vers MinIO dans l’agent`.
- Ne jamais committer de secrets. Les mots de passe et les clés restent dans des fichiers `.env`, listés dans le `.gitignore`.