# CampusFix

Plateforme intelligente de signalement et de gestion des problèmes dans les établissements universitaires.

## Description

Un étudiant découvre un problème sur le campus (projecteur en panne, fuite d'eau,
Wi-Fi qui ne marche pas, climatiseur en panne...). Avec CampusFix, il signale le
problème depuis l'application. Le responsable de maintenance reçoit le signalement,
l'affecte à un technicien et suit l'intervention jusqu'à sa résolution.
L'utilisateur est notifié à chaque changement important.

Processus métier : signalement → affectation → intervention → résolution → notification.

## Acteurs

- **Étudiant / Personnel** : signaler un problème, suivre son état, donner un avis
- **Technicien** : consulter ses interventions, ajouter un compte rendu, confirmer la réparation
- **Responsable de maintenance** : définir la priorité, affecter un technicien, consulter les statistiques
- **Administrateur** : gérer les utilisateurs, les bâtiments, les salles, les équipements

## Fonctionnalités principales

- Authentification et gestion des profils
- Gestion des bâtiments, des salles et des équipements
- Création et suivi des signalements
- Priorisation et affectation aux techniciens
- Suivi des interventions et gestion du stock de pièces
- Notifications
- Statistiques

## Architecture

Architecture microservices avec API Gateway, une base de données indépendante par service.

| Microservice | Responsabilité | Base de données | Responsable |
|---|---|---|---|
| user-service | Comptes, rôles, authentification | MySQL | Nom Prénom 1 |
| location-service | Bâtiments et salles | MySQL | Nom Prénom 2 |
| equipment-service | Équipements et pièces de rechange | PostgreSQL | Nom Prénom 3 |
| incident-service | Signalements | PostgreSQL | Nom Prénom 4 |
| assignment-service | Affectations | MySQL | Nom Prénom 5 |
| intervention-service | Réparations | PostgreSQL | À définir |
| notification-service | Notifications | MongoDB | À définir |

Communications :
- Synchrone : Incident Service → Location Service (vérification de la salle)
- Asynchrone : Assignment Service → Notification Service (événement `IncidentAssigned`)

## Technologies

- Backend : Java, Spring Boot
- Frontend : Angular / React
- API Gateway : Spring Cloud Gateway
- Sécurité : Keycloak
- Messaging : RabbitMQ
- Conteneurisation : Docker

## Structure du dépôt

- `Backend/` : les microservices
- `Frontend/` : l'application cliente
- `Documentation/Presentation/` : présentation de la séance 4
- `Documentation/Diagrams/` : diagramme d'architecture globale et diagrammes du projet
- `Documentation/Document_Technique/` : dossier technique

## Classe / Groupe

4SSA9 - G1
