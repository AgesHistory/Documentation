# Créer un Topic

Crée un nouveau topic sur le forum.

- **Méthode** : POST
- **Endpoint** : `/topic/create`
- **En-tête (Headers)** :
  - `Authorization` : Token JWT de l'utilisateur connecté.

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
- **Endpoint** : `/topic/delete/:id`
- **En-tête (Headers)** :
  - `Authorization` : Token JWT de l'utilisateur connecté.

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
- **Endpoint** : `/topic/:id`
- **En-tête (Headers)** :
  - `Authorization` : Token JWT de l'utilisateur connecté.

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

## Récupérer les Topics

Récupère les topics du forum.

- **Méthode** : GET
- **Endpoint** : `/topics`
- **En-tête (Headers)** :
  - `Authorization` : Token JWT de l'utilisateur connecté.

- **Réponse en cas de succès** : Code `200 OK`

  ```json
  {
    "success": true,
    "message": "Topics récupérés avec succès.",
    "topics": [
      {
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
		"tags": ["test","salut"]
      },
      {...}
    ]
  }
  ```
- **Codes d'erreur** :
    - Code `401 Unauthorized` : Si l'utilisateur n'est pas authentifié.
    - Code `500 Internal Server Error` : Si une erreur inattendue se produit.

## Récupérer les Topics d'un Utilisateur et via un Tag

Récupère les topics d'un utilisateur spécifié par son ID.

- **Méthode** : GET
- **Endpoint** : `/topics/user/:id` ou `/topics/tag/:tag`
- **En-tête (Headers)** :
  - `Authorization` : Token JWT de l'utilisateur connecté.

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


## Modifier un Topic

Modifie un topic spécifié par son ID.

- **Méthode** : PUT
- **Endpoint** : `/topic/:id`
- **En-tête (Headers)** :
  - `Authorization` : Token JWT de l'utilisateur connecté.

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

    