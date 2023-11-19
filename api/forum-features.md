# Forum
Cette catégorie contient les informations générales, les tendances, la recherche...


## Récupérer les Topics

Récupère les topics du forum.

- **Méthode** : GET
- **Endpoint** : `/topic`
- **En-tête (Headers)** :
  - `Authorization` : Token JWT de l'utilisateur connecté.
- **Query**:
  - `start`: à partir de quel topic commencer à les récupérer
  - `end`: à partir de quel topic arreter de les récupérer

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


## Afficher Les tendances

Récupère les tendances

- **Méthode** : GET
- **Endpoint** : `/topic/tendance`
- **En-tête (Headers)** :
  - `no content`
- **Query**:
  - `start`: à partir de quel topic commencer à les récupérer
  - `end`: à partir de quel topic arreter de les récupérer

### Réponse en cas de succès

- Code : `200 OK`

```json
{
	"code": 200,
	"message": {
		"popularTags": [
            "history",
			"art"
		],
		"popularTopics": [
			{
				"staffs": [],
				"_id": "7108872993752748032",
				"name": "Topic de test",
				"description": "salut ceci est un topic",
				"content": "Topic sur l'histoire de l'art",
				"likes": [],
				"dislikes": [],
				"share": [],
				"views": 0,
				"tags": [
					"history",
					"art"
				],
				"edited": false,
				"comments": [],
				"owner": "7102951221928923000",
				"createdAt": "2023-09-16T18:03:06.429Z"
			}
		],
		"recentTopics": [
			{
				"staffs": [],
				"_id": "7108872993752748032",
				"name": "Topic de test",
				"description": "salut ceci est un topic",
				"content": "Topic sur l'histoire de l'art",
				"likes": [],
				"dislikes": [],
				"share": [],
				"views": 0,
				"tags": [
					"history",
					"art"
				],
				"edited": false,
				"comments": [],
				"owner": "7102951221928923000",
				"createdAt": "2023-09-16T18:03:06.429Z"
			}
		],
		"trendingTopics": []
	}
}
```

- Codes d'erreur
    - Code `500 Internal Server Error` : Si une erreur inattendue se produit.

## Récupérer les Topics liés à une recherche.

Récupère les topics contenant les lettres inclues dans la recherche.

- **Méthode** : GET
- **Endpoint** : `/topic/search/:text`
- **En-tête (Headers)** :
  - `Authorization` : Token JWT de l'utilisateur connecté.

- **Réponse en cas de succès** : Code `200 OK`

text: histo
```json
  {
	"code": 200,
	"message": [
		{
			"staffs": [],
			"_id": "7108872993752748032",
			"name": "Topic de test",
			"description": "salut ceci est un topic",
			"content": "Topic sur l'histoire de l'art",
			"likes": [],
			"dislikes": [],
			"share": [],
			"views": 0,
			"tags": [
				"history",
				"art"
			],
			"edited": false,
			"comments": [],
			"owner": "7102951221928923000",
			"createdAt": "2023-09-16T18:03:06.429Z"
		}, {...}
	]
}
```
- **Codes d'erreur** :
    - Code `401 Unauthorized` : Si l'utilisateur n'est pas authentifié.
    - Code `500 Internal Server Error` : Si une erreur inattendue se produit.

