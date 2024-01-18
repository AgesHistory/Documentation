# Créer un Topic

Crée un nouveau topic sur le forum.

- **Méthode** : POST
- **Endpoint** : `https://ageshistory.com/api/topic/create`
- **En-tête (Headers)** :
  - `authorization` : Token JWT de l'utilisateur connecté.

## Paramètres du Corps (Body)

- **`name`** (obligatoire) : Le nom du topic.
- **`description`** : La description du topic (facultatif).
- **`content`** (obligatoire) : Le contenu du topic.
- **`tags`** : Les tags du topic (facultatif).

## Réponse en cas de succès

- Code : `201 Created`
- Contenu JSON de la réponse :

```json
{
  "success": true,
  "message": "Topic créé avec succès.",
  "topic": {
    "_id": "ID_du_topic",
    "name": "Nom_du_topic",
    "description": "Description_du_topic",
    "content": "Contenu_du_topic",
    "owner": "ID_du_propriétaire",
    "CreatedAt": "Date_de_création_du_topic"
  }
}
```

- Codes d'erreur

    - Code `400 Bad Request` : Si le nom du topic n'est pas spécifié.
    - Code `401 Unauthorized` : Si l'utilisateur n'est pas authentifié.
    - Code `500 Internal Server Error` : Si une erreur inattendue se produit.

## Supprimer un Topic

Supprime un topic spécifié par son ID.

- **Méthode** : DELETE
- **Endpoint** : `https://ageshistory.com/api/topic/:id`
- **En-tête (Headers)** :
  - `authorization` : Token JWT de l'utilisateur connecté.

- **Réponse en cas de succès** : Code `200 OK`

  ```json
  {
    "success": true,
    "message": "Topic supprimé avec succès."
  }
  ```

- **Codes d'erreur** :
    - Code `401 Unauthorized` : Si l'utilisateur n'est pas authentifié.
    - Code `404 Not Found` : Si le topic n'est pas trouvé.
    - Code `500 Internal Server Error` : Si une erreur inattendue se produit.

## Récupérer un Topic

Récupère un topic spécifié par son ID.

- **Méthode** : GET
- **Endpoint** : `https://ageshistory.com/api/topic/:id`
- **En-tête (Headers)** :
  - `authorization` : Token JWT de l'utilisateur connecté.

- **Réponse en cas de succès** : Code `200 OK`

  ```json
  {
    "success": true,
    "message": "Topic récupéré avec succès.",
    "topic": {
      "_id": "ID_du_topic",
      "name": "Nom_du_topic",
      "description": "Description_du_topic",
      "content": "Contenu_du_topic",
      "owner": "ID_du_propriétaire",
      "CreatedAt": "Date_de_création_du_topic"
    }
  }
  ```
- **Codes d'erreur** :
    - Code `401 Unauthorized` : Si l'utilisateur n'est pas authentifié.
    - Code `404 Not Found` : Si le topic n'est pas trouvé.
    - Code `500 Internal Server Error` : Si une erreur inattendue se produit.


## Modifier un Topic

Modifie un topic spécifié par son ID.

- **Méthode** : PUT
- **Endpoint** : `https://ageshistory.com/api/topic/:id`
- **En-tête (Headers)** :
  - `authorization` : Token JWT de l'utilisateur connecté.

## Paramètres du Corps (Body)

- **`name`** : Le nom du topic (facultatif).
- **`description`** : La description du topic (facultatif).
- **`content`** : Le contenu du topic (facultatif).
- **`tags`** : Les tags du topic (facultatif).

## Réponse en cas de succès

- Code : `200 OK`

```json
{
    "code": 200,
    "message": {
        "_id": "ID_du_topic",
        "name": "Nom_du_topic",
        "description": "Description_du_topic",
        "content": "Contenu_du_topic",
        "likes": [],
        "dislikes": [],
        "share": [],
        "views": "Nombre_de_vues_du_topic ( Number )",
        "edited": "Boolean",
        "comments": [
            "ID_du_commentaire",
            "ID_du_commentaire2"
        ],
        "owner": 7101254393973969000,
        "createdAt": "2023-08-29T21:49:28.438Z"
    }
}
```

- Codes d'erreur

    - Code `400 Bad Request` : Si le nom du topic n'est pas spécifié.
    - Code `401 Unauthorized` : Si l'utilisateur n'est pas authentifié.
    - Code `404 Not Found` : Si le topic n'est pas trouvé.
    - Code `500 Internal Server Error` : Si une erreur inattendue se produit.

## Récupérer les Topics d'un Utilisateur

Récupère les topics d'un utilisateur spécifié par son ID.

- **Méthode** : GET
- **Endpoint** : `/topic/user/:id`
- **En-tête (Headers)** :
  - `authorization` : Token JWT de l'utilisateur connecté.

- **Réponse en cas de succès** : Code `200 OK`

```json
  {
      "success": true,
      "message": "Topics récupérés avec succès.",
      "topics": [{
          "_id": "ID_du_topic",
          "name": "Nom_du_topic",
          "description": "Description_du_topic",
          "content": "Contenu_du_topic",
          "likes": [],
          "dislikes": [],
          "share": [],
          "views": "Nombre_de_vues_du_topic ( Number )",
          "edited": "Boolean",
          "comments": [
              "ID_du_commentaire",
              "ID_du_commentaire2"
          ],
          "owner": "ID_du_propriétaire",
          "createdAt": "timestamp",
          "tags": ["test", "salut"]
      }]
  }
```
- **Codes d'erreur** :
    - Code `401 Unauthorized` : Si l'utilisateur n'est pas authentifié.
    - Code `500 Internal Server Error` : Si une erreur inattendue se produit.


## Liker/disliker/partager un topic

Ces requêtes vous permettent de liker, disliker et partager un topic.

- **Méthode** : POST
- **Endpoint** : `https://ageshistory.com/api/topic/:id/like` | `https://ageshistory.com/api/topic/:id/dislike` | `https://ageshistory.com/api/topic/:id/share`
- **En-tête (Headers)** :
  - `authorization` : Token JWT de l'utilisateur connecté.

- **Réponse en cas de succès** : Code `200 OK`

Like/Dislike: 
```json
{
	"code": 200,
	"message": "You liked this topic" || "You disliked this topic"
}
```

Share:
```json
{
	"code": 200,
	"message": {
		"url": "http://localhost:8080/topic/7108873529478615040",
		"topic": {
			"_id": "7108873529478615040",
			"name": "New Topic",
			"description": "salut ceci est un nouveau topic",
			"content": "Topic sur l'histoire de l'art",
			"likes": [],
			"dislikes": [
				"7102951221928923136"
			],
			"share": [
				"7102951221928923136"
			],
			"views": 3,
			"tags": [],
			"edited": true,
			"comments": [
				"7108883606893760512",
				"7108883821117837312"
			],
			"owner": "7102951221928923136",
			"createdAt": "2023-09-16T18:05:13.892Z",
			"staffs": [
				"7103141925003202560"
			]
		}
	}
}
```

- **Codes d'erreur** :
    - Code `401 Unauthorized` : Si l'utilisateur n'est pas authentifié.
    - Code `500 Internal Server Error` : Si une erreur inattendue se produit.


## Ajouter un staff au topic

Cette requête vous permet d'ajouter un modérateur à vôtre topic
/!\ Vous devez être le fondateur du topic pour ajouter des modérateurs

- **Méthode** : POST
- **Endpoint** : `https://ageshistory.com/api/topic/:topicID/:staffID`
- **En-tête (Headers)** :
  - `authorization` : Token JWT de l'utilisateur connecté.

- **Réponse en cas de succès** : Code `200 OK`

```json
{
	"code": 200,
	"message": {
		"_id": "7108873529478615040",
		"name": "New Topic",
		"description": "salut ceci est un nouveau topic",
		"content": "Topic sur l'histoire de l'art",
		"likes": [],
		"dislikes": [
			"7102951221928923136"
		],
		"share": [
			"7102951221928923136"
		],
		"views": 2,
		"tags": [],
		"edited": true,
		"comments": [
			"7108883606893760512",
			"7108883821117837312"
		],
		"owner": "7102951221928923136",
		"createdAt": "2023-09-16T18:05:13.892Z",
		"staffs": [
			"7103141925003202560",
			"7102956217768611840"
		]
	}
}
```

- **Codes d'erreur** :
    - Code `401 Unauthorized` : Si l'utilisateur n'est pas authentifié.
    - Code `403 Forbidden` : Si le modérateur l'est déjà.
    - Code `404 no found` : Si le modérateur mentionné n'existe pas.
    - Code `500 Internal Server Error` : Si une erreur inattendue se produit.

## Supprimer un staff d'un topic

Cette requête vous permet de supprimer un modérateur de vôtre topic
/!\ Vous devez être le fondateur du topic pour ajouter des modérateurs

- **Méthode** : DELETE
- **Endpoint** : `https://ageshistory.com/api/topic/:topicID/:staffID`
- **En-tête (Headers)** :
  - `authorization` : Token JWT de l'utilisateur connecté.

- **Réponse en cas de succès** : Code `200 OK`

```json
{
	"code": 200,
	"message": {
		"_id": "7108873529478615040",
		"name": "New Topic",
		"description": "salut ceci est un nouveau topic",
		"content": "Topic sur l'histoire de l'art",
		"likes": [],
		"dislikes": [
			"7102951221928923136"
		],
		"share": [
			"7102951221928923136"
		],
		"views": 2,
		"tags": [],
		"edited": true,
		"comments": [
			"7108883606893760512",
			"7108883821117837312"
		],
		"owner": "7102951221928923136",
		"createdAt": "2023-09-16T18:05:13.892Z",
		"staffs": [
			"7103141925003202560"
		]
	}
}
```

- **Codes d'erreur** :
    - Code `401 Unauthorized` : Si l'utilisateur n'est pas authentifié.
    - Code `403 Forbidden` : Si la personne mentionnée n'est pas modérateur du topic.
    - Code `404 no found` : Si le modérateur mentionné n'existe pas.
    - Code `500 Internal Server Error` : Si une erreur inattendue se produit.

