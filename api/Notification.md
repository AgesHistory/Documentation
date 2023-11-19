# Notifications

Documentation des endpoints liés aux notifications.

## Obtention des notifications de l'Utilisateur Connecté

Récupère la liste de notifications de l'utilisateur actuellement connecté.

- **Méthode** : GET
- **Endpoint** : `/identity/@me/notifications`
- **En-tête (Headers)** :
  - `Authorization` : Token JWT de l'utilisateur connecté.

- **Réponse en cas de succès** : Code `200 OK`

```json
{
	"code": 200,
	"message": [
		{
			"id": "7122338918753636352",
			"type": 9,
			"content": "New Topic 7108873529478615040 ",
			"read": false,
			"createdAt": 1698097924890
		},
		{
			"id": "7132029486308003840",
			"type": 0,
			"content": "Ceci est une notification de test",
			"read": true,
			"createdAt": 1700408336238
		}
	]
}
```
- **Codes d'erreur** :
  - Code `401 Unauthorized` : Si l'utilisateur n'est pas authentifié.


## Obtention d'une notification en cible

Récupère une notification lié à vôtre compte actuellement connecté

- **Méthode** : GET
- **Endpoint** : `/identity/@me/notifications/:id`
- **En-tête (Headers)** :
  - `Authorization` : Token JWT de l'utilisateur connecté.

- **Réponse en cas de succès** : Code `200 OK`

/!\ retourne les notifications restantes
```json
{
	"code": 200,
	"message": [
		{
			"id": "7122870518205648896",
			"type": 9,
			"content": "New Topic 7108873529478615040 ",
			"read": false,
			"createdAt": 1698224668077
		},
		{
			"id": "7122872761076158464",
			"type": 9,
			"content": "New Topic 7108873529478615040 ",
			"read": false,
			"createdAt": 1698225202817
		}
	]
}
```
- **Codes d'erreur** :
  - Code `404 Not Found` : Si l'utilisateur n'est pas trouvé.
