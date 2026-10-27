# Portfolio en gestion des identités et des accès

> Les liens vidéo ouvrent les fichiers MP4 originaux en 1080p. GitHub peut lancer leur téléchargement; ouvrez ensuite le fichier pour regarder la vidéo en pleine qualité.

[English](README.md) | **Français**

Bonjour, je m’appelle Ted. Je travaille en service à la clientèle et en soutien technique dans une entreprise de logiciels, et je développe mes compétences en gestion des identités et des accès (IAM).

Ce portfolio présente cinq projets interreliés réalisés pour une entreprise fictive, Energy Retail Group (ERG). J’ai commencé par définir comment gérer les accès des employés, puis j’ai construit un laboratoire avec Active Directory, Okta, PowerShell et Microsoft Entra ID pour mettre ces principes en pratique.

Les projets couvrent la création de comptes, les changements de service, les revues des accès, l’authentification unique, l’authentification multifacteur et le retrait des accès lors des départs.

Les employés et les données d’entreprise sont fictifs. Les démonstrations techniques utilisent des systèmes de laboratoire fonctionnels.

**Langue des ressources :** cette page présente les projets en français. Les vidéos et la documentation détaillée accessibles ci-dessous sont en anglais.

## Explorer les projets

| Projet | Sujet | Documentation en anglais |
|---|---|---|
| 1 | Cycle de vie des identités et gouvernance des accès | [Consulter le projet 1](projects/01-identity-governance/) |
| 2 | Intégration d’Active Directory et d’Okta | [Consulter le projet 2](projects/02-active-directory-okta/) |
| 3 | Authentification unique SAML avec Okta | [Consulter le projet 3](projects/03-saml-single-sign-on/) |
| 4 | Revues des accès avec PowerShell | [Consulter le projet 4](projects/04-access-reviews/) |
| 5 | Cycle de vie des identités avec PowerShell et Microsoft Entra ID | [Consulter le projet 5](projects/05-entra-identity-lifecycle/) |

## Ce que je souhaitais démontrer

Mon objectif était de répondre à trois questions :

- Comment un nouvel employé reçoit-il les accès nécessaires à son travail?
- Comment ces accès évoluent-ils lorsqu’il change de poste?
- Comment retirer les accès lorsqu’il quitte l’entreprise?

Je voulais aussi montrer comment vérifier les résultats. La réussite d’une commande ne suffit pas : il faut confirmer l’état du compte, les appartenances aux groupes, l’affectation aux applications et les ressources auxquelles l’utilisateur peut réellement accéder.

## Environnement de laboratoire

J’ai utilisé les outils suivants dans les différents projets :

- Windows Server et Active Directory pour les utilisateurs, les unités organisationnelles et les groupes de sécurité.
- Okta et l’agent Okta Active Directory pour l’intégration de l’annuaire et l’authentification unique.
- Microsoft Entra ID et Cloud Sync pour le dernier projet d’identité hybride.
- PowerShell pour les modifications de comptes et les rapports de revue des accès.
- SAML 2.0 pour relier le portail ERG Business Portal à un fournisseur d’identité.
- L’accès conditionnel et Microsoft Authenticator pour démontrer l’authentification multifacteur (MFA).
- Excel et des diagrammes pour documenter les règles d’accès, les responsabilités et les cas de test.

Je prévoyais initialement d’utiliser Microsoft Entra ID pour toute la série, mais j’ai rencontré des difficultés pour activer la version d’essai. J’ai donc utilisé Okta pour les premiers projets techniques. Après avoir résolu le problème d’activation, j’ai réalisé le dernier projet avec Microsoft Entra ID.

<a id="projet-1"></a>

## Projet 1 — Cycle de vie des identités et gouvernance des accès

Avant de construire l’environnement technique, j’ai défini la manière dont ERG devait gérer les accès.

J’ai documenté les processus d’arrivée, de mutation et de départ, aussi appelés Joiner, Mover et Leaver :

- Arrivée : un nouvel employé reçoit les accès approuvés.
- Mutation : un employé change de rôle et reçoit les accès nécessaires à son nouveau poste.
- Départ : un employé quitte l’entreprise et ses accès sont retirés.

J’ai créé un catalogue d’accès qui associe les groupes aux différents rôles métier. J’ai également précisé qui demande, approuve, met en place et révise les accès.

Les documents comprennent un diagramme de processus, une matrice des responsabilités, une matrice des contrôles et des cas de test.

Ce projet porte sur la conception des processus. Les approbations et les résultats des tests sont simulés.

[Voir la démonstration du projet 1 — vidéo en anglais — 1080p MP4](https://github.com/teddylevent/erg-jml-governance/releases/download/portfolio-hd-v1/ERG-Project-1-Final.mp4) · [Consulter les documents et les preuves — en anglais](projects/01-identity-governance/)

<a id="projet-2"></a>

## Projet 2 — Intégration d’Active Directory et d’Okta

J’ai créé l’annuaire ERG dans Active Directory et l’ai relié à Okta à l’aide de l’agent Okta Active Directory.

J’ai créé des utilisateurs fictifs, des unités organisationnelles par service et des groupes de sécurité, puis importé les utilisateurs et groupes sélectionnés dans Okta.

Dans cet environnement, j’ai démontré :

- L’arrivée de Morgan Reed.
- La mutation d’Alex Carter des finances aux ventes.
- Le départ de Jamie Brooks.
- Un scénario d’accès privilégié temporaire pour Riley Chen.

J’ai vérifié les modifications des comptes et des groupes, puis examiné les informations d’audit disponibles dans Okta.

Ce projet m’a permis de comprendre l’effet des modifications de l’annuaire source sur la plateforme d’identité connectée.

[Voir le projet 2A — Configuration de l’annuaire et intégration — vidéo en anglais — 1080p MP4](https://github.com/teddylevent/erg-jml-governance/releases/download/portfolio-hd-v1/ERG-Project-2A-Final.mp4)

[Voir le projet 2B — Processus d’arrivée, de mutation et de départ — vidéo en anglais — 1080p MP4](https://github.com/teddylevent/erg-jml-governance/releases/download/portfolio-hd-v1/ERG-Project-2B-Final.mp4)

[Consulter le projet 2 — documentation en anglais](projects/02-active-directory-okta/)

<a id="projet-3"></a>

## Projet 3 — Authentification unique SAML avec Okta

J’ai relié le portail ERG Business Portal à Okta à l’aide de l’authentification unique SAML.

Le portail est une application de laboratoire personnalisée qui comporte des espaces de travail distincts par service. Il m’a permis de tester la connexion et les accès selon le service de l’utilisateur.

J’ai configuré les paramètres de confiance SAML, le certificat de signature, les attributs utilisateur et les informations de groupe, puis testé les accès dans le portail.

Ce projet démontre deux contrôles distincts :

- L’authentification vérifie l’identité de l’utilisateur.
- L’autorisation détermine les ressources auxquelles il peut accéder.

Okta authentifie l’utilisateur. Le portail valide la réponse SAML et utilise les informations de groupe reçues pour déterminer les accès.

Cette intégration utilise SAML pour la connexion et les autorisations fondées sur les groupes. Elle ne met pas en œuvre le provisionnement des comptes avec SCIM.

[Voir la démonstration du projet 3 — vidéo en anglais — 1080p MP4](https://github.com/teddylevent/erg-jml-governance/releases/download/portfolio-hd-v1/ERG-Project-3-Final.mp4) · [Consulter le projet 3 — documentation en anglais](projects/03-saml-single-sign-on/)

<a id="projet-4"></a>

## Projet 4 — Revues des accès avec PowerShell

J’ai utilisé PowerShell pour examiner des données fictives de comptes et d’accès stockées dans des fichiers CSV.

La revue comparait les renseignements sur les employés, les accès actuels et un référentiel de rôles approuvé.

Les contrôles recherchaient :

- Les comptes toujours actifs après la date de fin d’emploi.
- Les accès conservés après un départ.
- Les accès liés à un ancien service.
- Les accès privilégiés dont l’approbation était manquante ou expirée.
- Les accès ne correspondant pas au rôle approuvé de la personne.

Le script produisait des constats à examiner. J’ai consigné des décisions simulées et vérifié un jeu de données d’exemple corrigé.

Le script signale les exceptions; il ne retire pas automatiquement les accès. La démonstration utilise des données préparées et ne modifie aucun compte réel dans Active Directory ou Okta.

[Voir la démonstration du projet 4 — vidéo en anglais — 1080p MP4](https://github.com/teddylevent/erg-jml-governance/releases/download/portfolio-hd-v1/ERG-Project-4-Access-Review-Final.mp4) · [Consulter le projet 4 — documentation en anglais](projects/04-access-reviews/)

<a id="projet-5"></a>

## Projet 5 — Cycle de vie des identités avec PowerShell et Microsoft Entra ID

Pour le dernier projet, j’ai relié le laboratoire Active Directory à Microsoft Entra ID avec Cloud Sync. J’ai aussi relié le portail ERG Business Portal à Entra avec SAML.

J’ai suivi un employé fictif, Taylor Quinn, pendant tout son cycle de vie.

### Arrivée

J’ai créé Taylor dans Active Directory, mis à jour son profil et ajouté son compte aux groupes approuvés des finances et des employés.

Après avoir activé le compte et vérifié la synchronisation, j’ai testé sa connexion au portail. Taylor pouvait ouvrir l’espace de travail des finances, tandis que les espaces sans rapport avec son rôle étaient restreints.

### Accès conditionnel et MFA

J’ai évalué les stratégies de MFA et d’authentification héritée en mode rapport uniquement avant de les activer.

J’ai ensuite testé la MFA et examiné les journaux de connexion pour vérifier le résultat de la stratégie.

La connexion dans le navigateur a démontré l’application de la MFA. Il ne s’agissait pas d’un test avec un client utilisant l’authentification héritée.

### Mutation

J’ai transféré Taylor des finances aux ventes.

J’ai retiré son appartenance à l’ancien groupe des finances et ajouté le groupe approuvé des ventes. J’ai également modifié son service, son titre de poste, son gestionnaire et son unité organisationnelle dans Active Directory.

Après la synchronisation, je me suis reconnecté et j’ai vérifié que le portail affichait les ventes et autorisait l’accès au bon espace de travail.

### Départ

J’ai désactivé le compte Active Directory de Taylor, bloqué sa connexion dans le nuage, révoqué ses sessions et retiré ses groupes d’accès.

J’ai vérifié l’état du compte, les appartenances aux groupes, l’affectation à l’application et le résultat d’une nouvelle tentative de connexion.

PowerShell assurait les modifications de l’annuaire, tandis que Cloud Sync transmettait à Entra les modifications prises en charge. Certaines étapes d’administration et de vérification dans le nuage ont été réalisées manuellement.

Le test final a démontré le refus d’une nouvelle connexion. Il n’a pas démontré la fermeture immédiate d’une session du portail déjà ouverte.

[Voir la démonstration du projet 5 — vidéo en anglais — 1080p MP4](https://github.com/teddylevent/erg-jml-governance/releases/download/portfolio-hd-v1/ERG-Project-5-Final.mp4) · [Consulter le projet 5 — documentation en anglais](projects/05-entra-identity-lifecycle/)

## Ce que j’ai appris

Ces projets m’ont permis de comprendre que :

- Une unité organisationnelle et un groupe de sécurité ont des fonctions différentes.
- Le renseignement du service d’un employé ne lui accorde pas automatiquement des accès applicatifs.
- Un changement de rôle nécessite à la fois la mise à jour du profil et la modification des accès.
- La synchronisation de l’annuaire et les sessions applicatives sont des mécanismes distincts.
- Les stratégies en mode rapport uniquement évaluent les accès sans appliquer les contrôles configurés.
- La gestion d’un départ nécessite des vérifications dans l’annuaire, la plateforme d’identité et l’application.

J’ai également appris à analyser les problèmes à partir des propriétés des comptes, des appartenances aux groupes, des informations de synchronisation et des journaux de connexion.

## À propos du laboratoire

ERG est une entreprise fictive créée pour ce portfolio. Les projets utilisent des employés fictifs et des données d’entreprise d’exemple.

Les exercices de gouvernance et les revues de données d’exemple sont distingués des démonstrations techniques fonctionnelles.

## Contact

[LinkedIn](https://www.linkedin.com/in/tedweks/) · [GitHub](https://github.com/teddylevent)

