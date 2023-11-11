# Utilisateurs

Documentation des endpoints liés aux utilisateurs et aux profils.

## Obtention du Profil de l'Utilisateur Connecté

Récupère le profil de l'utilisateur actuellement connecté.

- **Méthode** : GET
- **Endpoint** : `/identity/@me`
- **En-tête (Headers)** :
  - `Authorization` : Token JWT de l'utilisateur connecté.

- **Réponse en cas de succès** : Code `200 OK`

```json
{
  "id": "user_id",
  "username": "john_doe",
  "email": "john@example.com",
  "type_account": "user",
  "private": false,
  "avatar": "avatar_url",
  "bio": "Description de l'utilisateur",
  "badges": ["badge1", "badge2"],
  "followers": 10,
  "following": 15,
  "topics": 5,
  "CreatedAt": "timestamp"
}
```
- **Codes d'erreur** :
  - Code `401 Unauthorized` : Si l'utilisateur n'est pas authentifié.


## Obtention du Profil d'un Utilisateur

Récupère le profil d'un utilisateur spécifié par son nom d'utilisateur ou son ID.

- **Méthode** : GET
- **Endpoint** : `/identity/@:username` ou `/identity/@:ID`
- **En-tête (Headers)** :
  - `Authorization` : Token JWT de l'utilisateur connecté.

- **Réponse en cas de succès** : Code `200 OK`

/!\ Si le compte de l'utilisateur est privé les abonnements, abonnés et les topics deviennent sous forme de numéro.

```json
{
  "id": "user_id",
  "username": "john_doe",
  "type_account": "user",
  "private": false,
  "avatar": "avatar_url",
  "bio": "Description de l'utilisateur",
  "badges": ["badge1", "badge2"],
  "followers": ["username", "username2"],
  "following": ["username", "username2"],
  "topics": ["Topic_ID", "Topic_ID2"],
  "CreatedAt": "timestamp"
}
```
- **Codes d'erreur** :
  - Code `404 Not Found` : Si l'utilisateur n'est pas trouvé.