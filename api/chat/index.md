# Message privés

Documentation des endpoints liés aux messages privés.

## Obtention des conversations

Récupère la liste des derniers messages pour former une liste de conversation.

- **Méthode** : GET
- **Endpoint** : `/messages/conversations/`
- **En-tête (Headers)** :
  - `authorization` : Token JWT de l'utilisateur connecté.

- **Réponse en cas de succès** : Code `200 OK`

```json
{
	"code": 200,
	"message": [
		{
			"id": "7102956217768611840",
			"username": "punchnox",
			"type_account": "user",
			"badges": [],
			"commonFriends": [],
			"private": false,
			"avatar": "http://localhost:8080/medias/avatar/7102956217768611840.png",
			"last_message": {
				"content": "Salut comment ça va"
			}
		}
	]
}
```
- **Codes d'erreur** :
  - Code `401 Unauthorized` : Si l'utilisateur n'est pas authentifié.



## Obtention d'une conversation

Récupère la liste des derniers messages d'une conversation mentionné.

- **Méthode** : GET
- **Endpoint** : `/messages/user/:id`
- **En-tête (Headers)** :
  - `authorization` : Token JWT de l'utilisateur connecté.

- **Réponse en cas de succès** : Code `200 OK`

```json
{
	"code": 200,
	"message": [
		{
			"_id": "7103858918018781184",
			"sender": "7103141925003202560",
			"receiver": "7102956217768611840",
			"content": "message de test 2",
			"edited": false,
			"react": null,
			"CreatedAt": "2023-09-02T21:56:28.113Z"
		},
		{
			"_id": "7103877426005938176",
			"sender": "7102956217768611840",
			"receiver": "7103141925003202560",
			"content": "mon super message de test!!!",
			"edited": false,
			"react": null,
			"CreatedAt": "2023-09-02T23:08:17.861Z"
		},
	]
}
```
- **Codes d'erreur** :
  - Code `401 Unauthorized` : Si l'utilisateur n'est pas authentifié.


## Envoyer un message/Créer une conversation

Envoie un message à l'utilisateur mentionné.

- **Méthode** : POST
- **Endpoint** : `/messages/user/:id`
- **En-tête (Headers)** :
  - `authorization` : Token JWT de l'utilisateur connecté.

- **Réponse en cas de succès** : Code `201 Created`

```json
{
	"code": 201,
	"message": {
		"sender": "7103141925003202560",
		"receiver": "7102956217768611840",
		"content": "Hello World",
		"edited": false,
		"react": null,
		"CreatedAt": "2023-11-19T21:56:45.077Z",
		"_id": "7132126230911913984"
	}
}
```
- **Codes d'erreur** :
  - Code `401 Unauthorized` : Si l'utilisateur n'est pas authentifié.
  - - Code `404 Not found` : Si l'utilisateur cible n'existe pas.

## Modifier un message

Modifie un de vos message dans un conversation cible.

- **Méthode** : PATCH
- **Endpoint** : `/messages/user/:UserId/:MessageId`
- **En-tête (Headers)** :
  - `authorization` : Token JWT de l'utilisateur connecté.

- **Réponse en cas de succès** : Code `200 OK`

```json
{
	"code": 200,
	"message": {
		"sender": "7103141925003202560",
		"receiver": "7102956217768611840",
		"content": "version modifié de mon message",
		"edited": true,
		"react": null,
		"CreatedAt": "2023-11-19T21:56:45.077Z",
		"_id": "7132126230911913984"
	}
}
```
- **Codes d'erreur** :
  - Code `401 Unauthorized` : Si l'utilisateur n'est pas authentifié.
  - Code `404 Not found` : Si la conversation n'existe pas ou que le message n'existe pas


## Supprimer un message

Supprime un de vos message dans une conversation mentionné.

- **Méthode** : DELETE
- **Endpoint** : `/messages/user/:UserId/:MessageId`
- **En-tête (Headers)** :
  - `authorization` : Token JWT de l'utilisateur connecté.

- **Réponse en cas de succès** : Code `200 OK`

```json
{
	"code": 200,
	"message": "Message deleted!"
}
```
- **Codes d'erreur** :
  - Code `401 Unauthorized` : Si l'utilisateur n'est pas authentifié.
  - Code `404 Not found` : Si la conversation n'existe pas ou que le message n'existe pas
