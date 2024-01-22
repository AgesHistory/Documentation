# Sanctions ( mute )
Documentation des routes administratives concernants les sanctions, seuls les utilisateurs ayant les permissions requises auront accès à ces fonctionnalités.

## Afficher si on a été sanctionné ( mute )

Permet de voir si vous avez reçu un mute ( disponible aux membres ) et si oui pour quelle raison.

- **Méthode** : GET
- **Endpoint** : `https://ageshistory.com/api/admin/mute/user/@me`
- **En-tête (Headers)** :
  - `authorization`:  Token JWT de l'utilisateur connecté.

### Paramètres du Corps (Body)
`no data`

### Réponse en cas de succès

- Code : `200 OK`

```json
{
	"code": 200,
	"message": {
		"user": {
			"id": "7102956217768611840",
			"username": "punchnox",
			"avatar": "https://ageshistory.com/api/medias/avatar/7102951221928923136.png"
		},
		"_id": "7102956217768611840",
		"reason": "Spam pub en message privé ",
		"admin": "punchnox",
		"CreatedAt": "2024-01-21T21:46:10.743Z"
	}
}
```
- Codes d'erreur
  - Code `401 Unauthorized` : Authorization invalide ou permissions manquantes.
  - Code `404 Not Found` : Si l'utilisateur n'a pas de sanction.
  - Code `500 Internal Server Error` : Si une erreur inattendue se produit.


## Afficher les tout les sanctions

Récupère tout les sanctions et leurs informations.

- **Méthode** : GET
- **Endpoint** : `https://ageshistory.com/api/admin/mute`
- **En-tête (Headers)** :
  - `authorization`:  Token JWT de l'utilisateur connecté.

### Paramètres du Corps (Body)
`no data`

### Réponse en cas de succès

- Code : `200 OK`

```json
{
	"code": 200,
	"message": [
		{
			"user": {
				"id": "7103141925003202560",
				"username": "bob",
				"avatar": "https://ageshistory.com/api/medias/avatar/7103141925003202560.png"
			},
			"_id": "7103141925003202560",
			"reason": "spam",
			"admin": "punchnox",
			"CreatedAt": "2024-01-21T21:46:10.743Z"
		},
		{
			"user": {
				"id": "7102956217768611840",
				"username": "punchnox",
				"avatar": "https://ageshistory.com/api/medias/avatar/7102951221928923136.png"
			},
			"_id": "7102956217768611840",
			"reason": "Spam pub en message privé ",
			"admin": "punchnox",
			"CreatedAt": "2024-01-21T21:46:10.743Z"
		}
	]
}
```
- Codes d'erreur
  - Code `401 Unauthorized` : Authorization invalide ou permissions manquantes.
  - Code `500 Internal Server Error` : Si une erreur inattendue se produit.


## Créer une sanction

Fait une sanction à l'adiministration de ageshistory.

- **Méthode** : POST
- **Endpoint** : `https://ageshistory.com/api/admin/mute/:id de l'utilisateur à mute`
- **En-tête (Headers)** :
  - `authorization`:  Token JWT de l'utilisateur connecté.

### Paramètres du Corps (Body)
```json
{
	"reason": "description du mute"
}
```


### Réponse en cas de succès

- Code : `201 Created`

```json
{
	"code": 200,
	"message": {
		"_id": "7103141925003202560",
		"reason": "spam",
		"admin": "punchnox",
		"user": {
			"id": "7103141925003202560",
			"username": "bob",
			"avatar": "https://ageshistory.com/api/medias/avatar/7103141925003202560.png"
		},
		"CreatedAt": "2024-01-21T21:39:19.836Z"
	}
}
```

- Codes d'erreur
  - Code `401 Unauthorized` : Authorization invalide.
  - Code `400 Bad Request` : Si des paramètres du corps (Body) sont manquant ou que l'utilisateur est déjà mute.
  - Code `500 Internal Server Error` : Si une erreur inattendue se produit.


## Afficher une sanction mentionné

Affiche les informations d'une sanction en particulier.

- **Méthode** : GET
- **Endpoint** : `https://ageshistory.com/api/admin/mute/:id`
- **En-tête (Headers)** :
  - `authorization`:  Token JWT de l'utilisateur connecté.

### Paramètres du Corps (Body)
`no data`

### Paramètres de l'URL
- `id`: L'identifiant dune sanction à supprimer

### Réponse en cas de succès

- Code : `200 OK`

```json
{
	"code": 200,
	"message": {
		"user": {
			"id": "7103141925003202560",
			"username": "bob",
			"avatar": "https://ageshistory.com/api/medias/avatar/7103141925003202560.png"
		},
		"_id": "7103141925003202560",
		"reason": "spam",
		"admin": "punchnox",
		"CreatedAt": "2024-01-21T21:39:19.836Z"
	}
}
```
- Codes d'erreur
  - Code `401 Unauthorized` : Authorization invalide ou permissions manquantes.
  - Code `404 Not Found` : Si l'id de l'utilisateur n'existe pas.
  - Code `500 Internal Server Error` : Si une erreur inattendue se produit.



## Supprimer une sanction

Supprime une sanction avec l'id fournit dans la requête.

- **Méthode** : DELETE
- **Endpoint** : `https://ageshistory.com/api/admin/mute/:id`
- **En-tête (Headers)** :
  - `authorization`:  Token JWT de l'utilisateur connecté.

### Paramètres du Corps (Body)
`no data`

### Paramètres de l'URL
- `id`: L'identifiant d'une sanction à supprimer

### Réponse en cas de succès

- Code : `200 OK`

```json
{
	"code": 200,
	"message": {
		"user": {
			"id": "7103141925003202560",
			"username": "bob",
			"avatar": "https://ageshistory.com/api/medias/avatar/7103141925003202560.png"
		},
		"_id": "7103141925003202560",
		"reason": "spam",
		"admin": "punchnox",
		"CreatedAt": "2024-01-21T21:39:19.836Z"
	}
}
```

- Codes d'erreur
  - Code `401 Unauthorized` : Authorization invalide.
  - Code `404 Not Found` : Si l'id de l'utilisateur n'existe pas.
  - Code `500 Internal Server Error` : Si une erreur inattendue se produit.



## Afficher les sanctions d'un utilisateur mentionné

Affiche tout si un utilisateur a été sanctionné, et si oui les informations de ce mute.

- **Méthode** : GET
- **Endpoint** : `https://ageshistory.com/api/admin/mute/user/:id`
- **En-tête (Headers)** :
  - `authorization`:  Token JWT de l'utilisateur connecté.

### Paramètres du Corps (Body)
`no data`

### Paramètres de l'URL
- `id`: L'identifiant de l'utilisateur visé

### Réponse en cas de succès

- Code : `200 OK`

```json
{
	"code": 200,
	"message": {
		"user": {
			"id": "7103141925003202560",
			"username": "bob",
			"avatar": "https://ageshistory.com/api/medias/avatar/7103141925003202560.png"
		},
		"_id": "7103141925003202560",
		"reason": "spam",
		"admin": "punchnox",
		"CreatedAt": "2024-01-21T21:46:10.743Z"
	}
}
```
- Codes d'erreur
  - Code `401 Unauthorized` : Authorization invalide ou permissions manquantes.
  - Code `404 Not Found` : Si l'id de l'utilisateur n'existe pas.
  - Code `500 Internal Server Error` : Si une erreur inattendue se produit.
