# demo-authserver-spring-authorization
Spring Authorization Server is a framework that provides implementations of the OAuth 2.1 and OpenID Connect 1.0 specifications and other related specifications. It is built on top of Spring Security to provide a secure, light-weight, and customizable foundation for building OpenID Connect 1.0 Identity Providers and OAuth2 Authorization Server products.


Ce fichier README.md fournit une documentation complète pour votre projet, incluant une description de chaque composant, des instructions d'installation et de configuration, ainsi que des informations sur l'utilisation et la personnalisation du serveur d'autorisation Spring.

# Spring Authorization Server - Configuration Minimale

Ce projet est une configuration minimale pour démarrer rapidement avec un serveur d'autorisation Spring. Il inclut les composants essentiels pour un serveur d'autorisation OAuth 2.1 fonctionnel.

## Table des matières

- [Aperçu](#aperçu)
- [Configuration requise](#configuration-requise)
- [Installation](#installation)
- [Configuration](#configuration)
- [Composants principaux](#composants-principaux)
    - [Chaîne de filtres Spring Security pour les points de terminaison du protocole](#chaîne-de-filtres-spring-security-pour-les-points-de-terminaison-du-protocole)
    - [Chaîne de filtres Spring Security pour l'authentification](#chaîne-de-filtres-spring-security-pour-lauthentification)
    - [UserDetailsService](#userdetailsservice)
    - [RegisteredClientRepository](#registeredclientrepository)
    - [JWKSource](#jwksource)
    - [KeyPair](#keypair)
    - [JwtDecoder](#jwtdecoder)
    - [AuthorizationServerSettings](#authorizationserversettings)
- [Utilisation](#utilisation)
- [Endpoints disponibles](#endpoints-disponibles)
- [Personnalisation](#personnalisation)
- [Sécurité](#sécurité)
- [Licence](#licence)

## Aperçu

Ce projet fournit une configuration minimale pour un serveur d'autorisation Spring, permettant de démarrer rapidement avec les fonctionnalités de base d'OAuth 2.1. Il est conçu pour être facile à comprendre et à étendre.

## Configuration requise

- Java 21 ou supérieur
- Maven 3.6 ou supérieur
- Spring Boot 3.x
- Spring Security 6.x
- Spring Authorization Server 1.x

## Installation

1. Clonez le dépôt :
   ```bash
   https://github.com/moustaphisene/demo-authserver-spring-authorization.git

2. Accédez au répertoire du projet :

       cd demo-authserver-spring-authorization

3. Construisez le projet avec Maven : 

       cd spring-auth-server
4. Exécutez l'application :

       mvn spring-boot\:run

- Configuration
Le projet utilise une configuration minimale définie dans la classe principale de l'application. Vous pouvez personnaliser la configuration en modifiant les beans définis dans cette classe.

- Composants principaux
Chaîne de filtres Spring Security pour les points de terminaison du protocole
Cette chaîne de filtres est responsable de la protection des points de terminaison du protocole OAuth 2.1, tels que /oauth2/authorize, /oauth2/token, et /oauth2/jwks. Elle est configurée pour autoriser uniquement les requêtes authentifiées et autorisées.

- Chaîne de filtres Spring Security pour l'authentification
Cette chaîne de filtres est responsable de l'authentification des utilisateurs. Elle est configurée pour utiliser le UserDetailsService pour récupérer les informations des utilisateurs et les authentifier.

- UserDetailsService
Le UserDetailsService est une interface Spring Security qui définit une méthode pour charger les détails de l'utilisateur à partir d'une source de données. Dans cette configuration minimale, il est implémenté pour retourner un utilisateur par défaut.

- RegisteredClientRepository
Le RegisteredClientRepository est une interface Spring Authorization Server qui définit des méthodes pour gérer les clients enregistrés. Dans cette configuration minimale, il est implémenté pour retourner un client par défaut.
- JWKSource
  Le JWKSource est une interface de la bibliothèque Nimbus JOSE + JWT qui définit des méthodes pour récupérer des clés JWK (JSON Web Key). Dans cette configuration minimale, il est utilisé pour signer les jetons d'accès.

- KeyPair
La KeyPair est une paire de clés publique et privée utilisée pour créer le JWKSource. Dans cette configuration minimale, les clés sont générées au démarrage de l'application.
- JwtDecoder
  Le JwtDecoder est une interface Spring Security qui définit une méthode pour décoder les jetons JWT (JSON Web Token). Dans cette configuration minimale, il est configuré pour utiliser la clé publique de la KeyPair pour décoder les jetons.
- AuthorizationServerSettings
  Le AuthorizationServerSettings est une classe Spring Authorization Server qui configure les paramètres du serveur d'autorisation, tels que l'URL de l'issuer.
- Utilisation
  Une fois l'application démarrée, vous pouvez utiliser les endpoints OAuth 2.1 pour obtenir des jetons d'accès et les utiliser pour accéder aux ressources protégées.

  - Endpoints or URIs disponibles

          http://localhost:9000/oauth2/authorize : Point de terminaison pour l'autorisation.
          http://localhost:9000/oauth2/token : Point de terminaison pour obtenir un jeton d'accès.
          http://localhost:9000/oauth2/jwks : Point de terminaison pour obtenir les clés JWK.
          http://localhost:9000/userinfo : Point de terminaison pour obtenir les informations de l'utilisateur.
          http://localhost:9000/.well-known/openid-configuration : Point de terminaison pour obtenir la configuration OpenID Connect.

- Personnalisation
Vous pouvez personnaliser la configuration en modifiant les beans définis dans la classe principale de l'application. Par exemple, vous pouvez ajouter des utilisateurs supplémentaires, des clients enregistrés, ou des scopes.

- Sécurité
Assurez-vous de configurer correctement la sécurité de votre serveur d'autorisation. Utilisez des mots de passe forts, des clés de signature sécurisées, et configurez correctement les politiques de sécurité.

- Licence
















