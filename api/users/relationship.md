# Relations d'Amis

Documentation des endpoints liés aux relations d'amis entre utilisateurs.

## Ajouter un Ami

Envoie une demande d'ami à un utilisateur spécifié.

- **Méthode** : POST
- **Endpoint** : `/user/relationships/:id`
- **En-tête (Headers)** :
  - `authorization` : Token JWT de l'utilisateur connecté.

- **Réponse en cas de succès** : Code `200 OK`

```json
{
  "message": "Demande d'ami envoyée avec succès."
}
```
- **Codes d'erreur** :
  - Code `401 Unauthorized` : Si l'utilisateur n'est pas authentifié.
  - Code `404 Not Found` : Si l'utilisateur n'est pas trouvé.
  - Code `409 Conflict` : Si l'utilisateur est déjà ami avec l'utilisateur spécifié.
  - Code `422 Unprocessable Entity` : Si l'utilisateur spécifié est l'utilisateur connecté.
  - Code `500 Internal Server Error` : Si une erreur inattendue se produit.


## Accepter une Demande d'Ami

Accepte une demande d'ami d'un utilisateur spécifié.

- **Méthode** : PATCH
- **Endpoint** : `/identity/@me/relationships/:id`
- **En-tête (Headers)** :
  - `authorization` : Token JWT de l'utilisateur connecté.

- **Réponse en cas de succès** : Code `200 OK`
  
  ```json
  {
    "message": "Demande d'ami acceptée avec succès."
  }
  ```

- **Codes d'erreur** :
  - Code `401 Unauthorized` : Si l'utilisateur n'est pas authentifié.
  - Code `404 Not Found` : Si l'utilisateur n'est pas trouvé.
  - Code `409 Conflict` : Si l'utilisateur est déjà ami avec l'utilisateur spécifié.
  - Code `422 Unprocessable Entity` : Si l'utilisateur spécifié est l'utilisateur connecté.
  - Code `500 Internal Server Error` : Si une erreur inattendue se produit.

## Refuser une Demande d'Ami ou Supprimer un Ami

Refuse une demande d'ami d'un utilisateur spécifié.

- **Méthode** : DELETE
- **Endpoint** : `/identity/@me/relationships/:id`
- **En-tête (Headers)** :
  - `authorization` : Token JWT de l'utilisateur connecté.

- **Réponse en cas de succès** : Code `200 OK`
  
  ```json
  {
    "message": "Demande d'ami refusée avec succès."
  }
  ```
  ou
  ```json
  {
    "message": "Ami supprimé avec succès."
  }```
- **Codes d'erreur** :
  - Code `401 Unauthorized` : Si l'utilisateur n'est pas authentifié.
  - Code `404 Not Found` : Si l'utilisateur n'est pas trouvé.
  - Code `422 Unprocessable Entity` : Si l'utilisateur spécifié est l'utilisateur connecté.
  - Code `500 Internal Server Error` : Si une erreur inattendue se produit.


## Récupérer les Demandes d'Amis

Récupère les demandes d'amis de l'utilisateur connecté.

- **Méthode** : GET
- **Endpoint** : `/identity/@me/relationships`
- **En-tête (Headers)** :
  - `authorization` : Token JWT de l'utilisateur connecté.

- **Réponse en cas de succès** : Code `200 OK`
  
  ```json
 {
	"code": 200,
	"message": {
		"friends": [
			{
				"id": "7103141925003202560",
				"username": "bob",
				"type": 0,
				"avatar": "7102951221928923136",
				"followers": 0,
				"following": 1,
				"commonFriends": []
			}
		],
		"friendRequests": [],
		"friendRequestsSent": []
	}
}
  ```
  
- **Codes d'erreur** :
  - Code `401 Unauthorized` : Si l'utilisateur n'est pas authentifié.
  - Code `500 Internal Server Error` : Si une erreur inattendue se produit.
