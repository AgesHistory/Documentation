# Créer un Commentaire

Crée un nouveau commentaire sur un topic cible.

- **Méthode** : POST
- **Endpoint** : `/topic/:id`
- **En-tête (Headers)** :
  - `Authorization` : Token JWT de l'utilisateur connecté.

## Paramètres du Corps (Body)
- **`content`** (obligatoire) : Le contenu du topic.

## Réponse en cas de succès

- Code : `201 Created`
- Contenu JSON de la réponse :

```json
{
	"code": true,
	"message": {
		"_id": "7132071092000133120",
		"author": "7102951221928923136",
		"content": "Hey ceci est un commentaire",
		"likes": [],
		"disklikes": [],
		"share": [],
		"edited": false,
		"createdAt": "2023-11-19T18:24:15.808Z"
	}
}
```

- Codes d'erreur

    - Code `400 Bad Request` : Si le contenu du commentaire n'est pas spécifié
    - Code `401 Unauthorized` : Si l'utilisateur n'est pas authentifié.
    - Code `500 Internal Server Error` : Si une erreur inattendue se produit.

## Supprimer un commentaire

Supprime un commentaire spécifié par son ID.

- **Méthode** : DELETE
- **Endpoint** : `/topic/:Topicid/:commentid`
- **En-tête (Headers)** :
  - `Authorization` : Token JWT de l'utilisateur connecté.

- **Réponse en cas de succès** : Code `200 OK`

  ```json
  {
    "success": true,
    "message": "Commentaire supprimé avec succès."
  }
  ```

- **Codes d'erreur** :
    - Code `401 Unauthorized` : Si l'utilisateur n'est pas authentifié.
    - Code `404 Not Found` : Si le commentaire n'est pas trouvé.
    - Code `500 Internal Server Error` : Si une erreur inattendue se produit.

## Récupérer un Commentaire

Récupère un commentaire spécifié par son ID.

- **Méthode** : GET
- **Endpoint** : `/topic/:Topicid/:Commentid`
- **En-tête (Headers)** :
  - `Authorization` : Token JWT de l'utilisateur connecté.

- **Réponse en cas de succès** : Code `200 OK`

```json
{
	"code": true,
	"message": {
		"_id": "7132071092000133120",
		"author": "7102951221928923136",
		"content": "Hey ceci est un commentaire",
		"likes": [],
		"disklikes": [],
		"share": [],
		"edited": false,
		"createdAt": "2023-11-19T18:24:15.808Z"
	}
}
```

- **Codes d'erreur** :
    - Code `401 Unauthorized` : Si l'utilisateur n'est pas authentifié.
    - Code `404 Not Found` : Si le commentaire n'est pas trouvé.
    - Code `500 Internal Server Error` : Si une erreur inattendue se produit.


## Modifier un Commentaire

Modifie un commentaire spécifié par son ID.

- **Méthode** : PUT
- **Endpoint** : `/topic/:Topicid/:Commentid`
- **En-tête (Headers)** :
  - `Authorization` : Token JWT de l'utilisateur connecté.

## Paramètres du Corps (Body)
- **`content`** : Le contenu du topic (facultatif).

## Réponse en cas de succès

- Code : `200 OK`

```json
{
	"code": true,
	"message": {
		"_id": "7132071092000133120",
		"author": "7102951221928923136",
		"content": "Hey ceci est un commentaire modifié",
		"likes": [],
		"disklikes": [],
		"share": [],
		"edited": true,
		"createdAt": "2023-11-19T18:24:15.808Z"
	}
}
```

- Codes d'erreur

    - Code `400 Bad Request` : Si le contenu du commentaire n'est pas spécifié.
    - Code `401 Unauthorized` : Si l'utilisateur n'est pas authentifié.
    - Code `404 Not Found` : Si le commentaire n'est pas trouvé.
    - Code `500 Internal Server Error` : Si une erreur inattendue se produit.


## Liker/disliker/partager un commentaire

Ces requêtes vous permettent de liker, disliker et partager un commentaire.

- **Méthode** : POST
- **Endpoint** : `/topic/:Topicid/:Commentid/like` | `/topic/:Topicid/:Commentid/dislike` | `/topic/:Topicid/:Commentid/share`
- **En-tête (Headers)** :
  - `Authorization` : Token JWT de l'utilisateur connecté.

- **Réponse en cas de succès** : Code `200 OK`

Like/Dislike: 
```json
{
	"code": 200,
	"message": "You liked this comment" || "You disliked this comment"
}
```

Share:
```json
{
	"code": 200,
	"message": {
		"url": "http://localhost:8080/topic/7108873529478615040/7132071092000133120",
		"comment": {
			"_id": "7132071092000133120",
			"author": "7102951221928923136",
			"content": "Hey ceci est un commentaire",
			"likes": [],
			"disklikes": [],
			"share": [
				"7102951221928923136"
			],
			"edited": false,
			"createdAt": "2023-11-19T18:24:15.808Z"
		}
	}
}
```

- **Codes d'erreur** :
    - Code `401 Unauthorized` : Si l'utilisateur n'est pas authentifié.
    - Code `404 Not Found` : Si le commentaire n'est pas trouvé.
    - Code `500 Internal Server Error` : Si une erreur inattendue se produit.