# BookStore API - ASP.NET Core & MongoDB

Ce projet est une API web basée sur des contrôleurs utilisant ASP.NET Core 9.0 et MongoDB pour la gestion d'une librairie.

## Fonctionnalités
- CRUD complet sur les livres (Books).
- Base de données NoSQL MongoDB.
- Authentification JWT.
- Autorisation basée sur les rôles (Admin requis pour les modifications).
- Documentation OpenAPI (Swagger).

## Prérequis
- .NET 9.0 SDK
- MongoDB 6.0+

## Configuration
Modifiez le fichier `appsettings.json` pour configurer la chaîne de connexion MongoDB :
```json
"BookStoreDatabase": {
  "ConnectionString": "mongodb://localhost:27017",
  "DatabaseName": "BookStore",
  "BooksCollectionName": "Books"
}
```

## Exécution locale
1. Clonez le dépôt.
2. Assurez-vous que MongoDB est démarré.
3. Exécutez la commande suivante à la racine du projet :
   ```bash
   dotnet run
   ```
4. L'API sera accessible sur `http://localhost:5000`.

## Utilisation de Docker
Pour exécuter l'application dans un container Docker :
```bash
docker build -t bookstoreapi .
docker run -d -p 8080:80 --name bookstore-api bookstoreapi
```

## Sécurité
- Les endpoints de lecture (`GET`) sont accessibles publiquement ou par tout utilisateur authentifié.
- Les endpoints de modification (`POST`, `PUT`, `DELETE`) nécessitent un jeton JWT avec le rôle `Admin`.
