# PRYMO DR Congo | Site V7 : Documentation API & scénarios de test

Site vitrine statique bilingue (FR/EN), responsive, à partir de la version V6 Mobile Money / Airtime.

## Nouveautés V7

- Ajout du menu « API & tests » et d'une zone de préparation des scénarios C2B/B2C dans la partie Mobile Money.
- Lien direct vers la documentation Swagger PRYMO : https://tppdrc.myone4all.com/api/docs#
- Choix du flux, de l'opérateur, de la devise et du montant fictif. Génération locale d'un **plan de test**, non d'une requête API.
- Accès à Swagger depuis le module, la FAQ et le pied de page.
- Suppression du faux exemple `POST /v1/collections` et de la réponse / du webhook arbitrairement inventés dans la version précédente.
- Révision des textes sur l'idempotence et les essais : la documentation effective et les validations de l'équipe PRYMO doivent faire foi.
- Préservation de la distinction Mobile Money (C2B/B2C) vs Airtime & Data prépayés, du drapeau de la RDC et des logos clients.

## Portée des tests

Ce site est une vitrine. Il **n'exécute aucun appel API, paiement ni décaissement**. Il ne reçoit, stocke, ni affiche aucun token API.

La documentation Swagger est un lien vers un système externe. La page Swagger est accessible, mais son contenu dynamique (méthodes, routes, schémas JSON, modes d'authentification, environnements) n'a pas pu être récupéré et confirmé dans l'environnement de réalisation. **Ne pas prendre les scénarios affichés par le site pour des requêtes conformes au contrat d'API.**

Pour réaliser les appels d'essai réels, le développeur doit :

1. Ouvrir la documentation PRYMO via le bouton sur le site.
2. Identifier les endpoints C2B/B2C et la méthode d'authentification officiellement décrite.
3. Obtenir de PRYMO l'accès à un environnement de test autorisé et les identifiants correspondants, via un canal sûr.
4. Vérifier le comportement pour chaque opérateur (selon les services activés), les devises autorisées, les statuts et les erreurs, y compris les essais de reprise et les cas de doublons.
5. Faire les appels uniquement depuis un client API sécurisé ou un backend, jamais depuis un navigateur public avec des secrets.
6. Valider séparément l'environnement de production et les conditions d'accès avant le lancement.

Consulter également `API-TEST-PLAN.md` pour la matrice de tests proposée.

## Vérifications de la V7

- Validation syntaxique JavaScript.
- Contrôle des assets locaux, des liens de documentation présents et des ancres utilisées.
- Essais navigateur (mise à jour des scénarios C2B/B2C, choix opérateurs, switch FR/EN) en vues desktop et mobile.
- Vérification de l'absence de débordement horizontal aux dimensions testées.

## Déploiement

Déposer `index.html`, `assets/` et `CNAME` (si GitHub Pages est utilisé) sur l'hébergement de `prymodrc.com`. Ne pas copier uniquement `index.html`, les médias sont des fichiers locaux.

Avant toute mise en production : vérifier les mentions réglementaires, autorisations des logos clients, coordonnées de contact, disponibilité des services et réception des formulaires de contact. Le formulaire utilise actuellement FormSubmit.
