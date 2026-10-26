# PRYMO API | Plan de tests proposé pour les développeurs

**Référence de l'API :** https://tppdrc.myone4all.com/api/docs#

**Règle de référence :** suivre la documentation PRYMO pour les chemins réels, champs requis, autorisations, signatures, codes d'erreur et schémas de réponse. Le site public ne fait aucun appel API.

| Domaine | Scénario | Résultat à vérifier |
| --- | --- | --- |
| Accès | Accès de test autorisé et authentification | Succès contrôlé; aucune clé exposée côté navigateur |
| C2B | Encaissement de test chez chaque opérateur activé | Statut, identifiant de transaction, montant, devise et journalisation |
| B2C | Décaissement de test vers chaque opérateur activé | Réception du statut final et rapprochement du montant |
| Statuts | Transaction en attente, validée, rejetée, annulée selon l'API | Transitions cohérentes avec la documentation |
| Validation | Devise, téléphone, montant, référence invalides | Rejet prévisible et message d'erreur exploitable |
| Droits | Opérateur ou service non activé | Contrôle d'accès approprié |
| Reprise | Timeout ou perte de réseau avant confirmation | Reconciliation des statuts avant toute nouvelle tentative |
| Doublons | Deux soumissions avec la même référence | Comportement conforme à la stratégie officielle de duplication/idempotence |
| Notifications | Callbacks/webhooks, **si** décrits dans Swagger | Schéma, sécurité et mécanisme de reprise conformes à la doc |
| Sécurité | Secrets, journaux et données clients | Clés non exposées, numéros masqués, transport chiffré |
| Mise en production | Passage du test au live | Validation humaine explicite et paramètres d'environnement indépendants |

### Opérateurs et canaux

Mobile Money : Vodacom M-Pesa, Airtel Money, Orange Money, Africell AfriMoney, **selon l'activation contractuelle**. Prévoir un protocole distinct pour Airtime / Data prépayés, sans le mélanger aux flux financiers C2B/B2C.

### Limites de vérification

Le lien Swagger est fourni par le propriétaire du site. La documentation interactive n'était pas disponible sous une forme textuelle exploitable lors de cette édition. Aucun nom d'endpoint, entête d'authentification, payload ou code HTTP n'a donc été déduit ou inventé.
