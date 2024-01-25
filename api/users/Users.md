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
		"banner": "https://ageshistory.com/api/medias/banner/7139011401229537280.png",
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
		"banner": "https://ageshistory.com/api/medias/banner/7139011401229537280.png",
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



## Ajouter ou modifier sa photo de profile

Permet d'ajouter ou changer la photo de profile de l'utilisateur connecté

- **Méthode** : POST
- **Endpoint** : `https://ageshistory.com/api/medias/avatar/`
- **En-tête (Headers)** :
  - `authorization` : Token JWT de l'utilisateur connecté.

- **Body (Type: Multipart)**:

- **Réponse en cas de succès** : Code `201 Created`


**Exemple Code** (nodejs: request):
```js
const fs = require('fs');
const request = require('request');

const options = {
  method: 'POST',
  url: 'https://ageshistory.com/api/medias/avatar/',
  headers: {
    'Content-Type': 'multipart/form-data; boundary=---011000010111000001101001',
    authorization: 'SuperSecretAuthorization'
  },
  formData: {
    avatar: {
      value: fs.createReadStream('chemin\\vers\\votre\\avatar.jpg'),
      options: {
        filename: 'chemin\\vers\\votre\\avatar.jpg',
        contentType: null
      }
    }
  }
};

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

- **Codes d'erreur** :
  - Code `401 Unauthorized` : Si l'utilisateur n'est pas authentifié.
  - Code `404 Not Found` : Si l'utilisateur n'est pas trouvé.


## Ajouter ou modifier sa photo de profile

Permet d'ajouter ou changer la photo de profile de l'utilisateur connecté

- **Méthode** : GET
- **Endpoint** : `https://ageshistory.com/api/medias/avatar/:id`
- **En-tête (Headers)** :
  - `authorization` : Token JWT de l'utilisateur connecté.

- **Body (Type: Multipart)**:

- **Réponse en cas de succès** : Code `200 OK`
- **Content-type**: `image/format`, ex: `image/png`

- **Codes d'erreur** :
  - Code `401 Unauthorized` : Si l'utilisateur n'est pas authentifié.
  - Code `404 Not Found` : Si l'utilisateur n'est pas trouvé.



## Ajouter ou modifier sa bannière

Permet de changer ou modifier la bannière du profile de l'utilisateur connecté

- **Méthode** : POST
- **Endpoint** : `https://ageshistory.com/api/medias/banner/`
- **En-tête (Headers)** :
  - `authorization` : Token JWT de l'utilisateur connecté.

- **Body (Type: Multipart)**:

- **Réponse en cas de succès** : Code `201 Created`


**Exemple Code** (nodejs: request):
```js
const fs = require('fs');
const request = require('request');

const options = {
  method: 'POST',
  url: 'https://ageshistory.com/api/medias/banner/',
  headers: {
    'Content-Type': 'multipart/form-data; boundary=---011000010111000001101001',
    authorization: 'SuperSecretAuthorization'
  },
  formData: {
    avatar: {
      value: fs.createReadStream('chemin\\vers\\votre\\bannière.jpg'),
      options: {
        filename: 'chemin\\vers\\votre\\bannière.jpg',
        contentType: null
      }
    }
  }
};

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

- **Codes d'erreur** :
  - Code `401 Unauthorized` : Si l'utilisateur n'est pas authentifié.
  - Code `404 Not Found` : Si l'utilisateur n'est pas trouvé.


## Ajouter ou modifier sa photo de profile

Permet d'ajouter ou changer la photo de profile de l'utilisateur connecté

- **Méthode** : GET
- **Endpoint** : `https://ageshistory.com/api/medias/banner/:id`
- **En-tête (Headers)** :
  - `authorization` : Token JWT de l'utilisateur connecté.

- **Body (Type: Multipart)**:

- **Réponse en cas de succès** : Code `200 OK`
- **Content-type**: `image/format`, ex: `image/png`

- **Codes d'erreur** :
  - Code `401 Unauthorized` : Si l'utilisateur n'est pas authentifié.
  - Code `404 Not Found` : Si l'utilisateur n'est pas trouvé.
