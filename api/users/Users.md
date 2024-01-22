# Utilisateurs

Documentation des endpoints liés aux utilisateurs et aux profils.

## Obtention du Profil de l'Utilisateur Connecté

Récupère le profil de l'utilisateur actuellement connecté.

- **Méthode** : GET
- **Endpoint** : `/identity/@me`
- **En-tête (Headers)** :
  - `authorization` : Token JWT de l'utilisateur connecté.
- **Paramètres de l'URL ( Query ) :**
  - `permission`: true. Cela permet d'afficher les permissions clairement. ( FACULTATIF )


- **Réponse en cas de succès** : Code `200 OK`

```json
{
	"code": 200,
	"message": {
		"id": "7102956217768611840",
		"username": "punchnox",
		"email": "supersecret@secret.com",
		"type_account": "developer",
		"private": false,
		"avatar": "https://ageshistory.com/api/medias/avatar/7102951221928923136.png",
		"bio": "Je suis un simple développeur\nJavaScript ( nodejs ), golang, python, elixir",
		"badges": [
			"owner",
			"dev"
		],
		"friends": [
			"7103141925003202560"
		],
		"friendRequests": [],
		"friendRequestsSent": [
			"7102951221928923136"
		],
		"permissions": 17372760,
		"followers": [
			"7102951221928923136",
			"7103141925003202560"
		],
		"following": [],
		"topics": [
			"7142462430658957312"
		],
		"CreatedAt": "2023-08-31T10:11:38.413Z"
	}
}
```
**Si l'url contient `?permission=true` :**
```json
{
	"code": 200,
	"message": {
		"id": "7102956217768611840",
		"username": "punchnox",
		"email": "supersecret@secret.com",
		"type_account": "developer",
		"private": false,
		"avatar": "https://ageshistory.com/api/medias/avatar/7102951221928923136.png",
		"bio": "Je suis un simple développeur\nJavaScript ( nodejs ), golang, python, elixir",
		"badges": [
			"owner",
			"dev"
		],
		"friends": [
			"7103141925003202560"
		],
		"friendRequests": [],
		"friendRequestsSent": [
			"7102951221928923136"
		],
		"permissions": [
			"BAN",
			"BAN_IP",
			"WARNINGS",
			"UNBAN",
			"VIEW_BAN",
			"MANAGE_ROLES",
			"MANAGE_MESSAGES",
			"LOCK_FORUM",
			"CREATE_DELETE_MODIFY_THREADS"
		],
		"followers": [
			"7102951221928923136",
			"7103141925003202560"
		],
		"following": [],
		"topics": [
			"7142462430658957312"
		],
		"CreatedAt": "2023-08-31T10:11:38.413Z"
	}
}
```

- **Codes d'erreur** :
  - Code `401 Unauthorized` : Si l'utilisateur n'est pas authentifié.


## Obtention du Profil d'un Utilisateur

Récupère le profil d'un utilisateur spécifié par son nom d'utilisateur ou son ID.

- **Méthode** : GET
- **Endpoint** : `/identity/@:username` ou `/identity/@:ID`
- **En-tête (Headers)** :
  - `authorization` : Token JWT de l'utilisateur connecté.

- **Réponse en cas de succès** : Code `200 OK`

/!\ Si le compte de l'utilisateur est privé les abonnements, abonnés et les topics deviennent sous forme de numéro.
```json
{
	"code": 200,
	"message": {
		"id": "7139011401229537280",
		"username": "Thor",
		"type_account": "user",
		"private": false,
		"avatar": "https://ageshistory.com/api/medias/avatar/7139011401229537280.png",
		"badges": [],
		"followers": [],
		"following": [],
		"topics": [],
		"permissions": 24,
		"friends": 0,
		"commonFriends": [],
		"CreatedAt": "2023-12-07T06:24:28.767Z"
	}
}
```

**Si l'url contient `?permission=false` :**
```json
{
	"code": 200,
	"message": {
		"id": "7139011401229537280",
		"username": "Thor",
		"type_account": "user",
		"private": false,
		"avatar": "https://ageshistory.com/api/medias/avatar/7139011401229537280.png",
		"badges": [],
		"followers": [],
		"following": [],
		"topics": [],
		"permissions": [
			"BAN",
			"BAN_IP"
		],
		"friends": 0,
		"commonFriends": [],
		"CreatedAt": "2023-12-07T06:24:28.767Z"
	}
}
```
- **Codes d'erreur** :
  - Code `404 Not Found` : Si l'utilisateur n'est pas trouvé.
