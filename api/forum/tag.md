# Tags
Les tags vous permettent de trouver des topics plus facilement, les ordonner dans de catégories bien distinctes et de repérer un topic venant d'une catégorie officiel et non-officiel.

## Afficher toutes les catégories

Récupère toutes les catégories et leurs spécificités.

- **Méthode** : GET
- **Endpoint** : `https://ageshistory.com/api/topic/categories`
- **En-tête (Headers)** :
  - `no content`

### Paramètres du Corps (Body)
`no data`

### Réponse en cas de succès

- Code : `200 OK`

```json
{
	"code": 200,
	"message": [
		{
			"color": "#fff",
			"name": "Technologie"
		},
		{
			"color": "#fff",
			"name": "Other"
		}
	]
}
```

- Codes d'erreur
    - Code `500 Internal Server Error` : Si une erreur inattendue se produit.



## Afficher tout les tags

Récupère tout les tags et leurs spécificités.

- **Méthode** : GET
- **Endpoint** : `https://ageshistory.com/api/topic/tag`
- **En-tête (Headers)** :
  - `no content`

### Paramètres du Corps (Body)
`no data`

### Réponse en cas de succès

- Code : `200 OK`

```json
{
	"code": 200,
	"message": {
		"Technologie": [
			{
				"author": {
					"id": "7102956217768611840",
					"username": "punchnox"
				},
				"_id": "7140368167045435392",
				"name": "My First Tag",
				"official": true,
				"CreatedAt": "2023-12-12T15:53:41.199Z"
			},
			{
				"author": {
					"id": "7102956217768611840",
					"username": "punchnox"
				},
				"_id": "7140368256853872640",
				"name": "robots",
				"official": true,
				"CreatedAt": "2023-12-12T15:53:41.199Z"
			}
		],
		"Other": [
			{
				"author": {
					"id": "7102956217768611840",
					"username": "punchnox"
				},
				"_id": "7140378788918988800",
				"name": "video games",
				"official": true,
				"CreatedAt": "2023-12-12T16:35:40.568Z"
			}
		]
	}
}
```

- Codes d'erreur
    - Code `500 Internal Server Error` : Si une erreur inattendue se produit.

    

## Créer un tag

Vous permet de créer un tag et le proposer à toute la communauté.

- **Méthode** : POST
- **Endpoint** : `https://ageshistory.com/api/topic/tag/`
- **En-tête (Headers)** :
  - `no content`

### Paramètres du Corps (Body)
- **`name`** (obligatoire) : Le nom du tag.
```json
{
	"name": "video games",
	"categorie": "Other"
}
```

### Réponse en cas de succès

- Code : `201 Created`

```json
{
	"code": 201,
	"message": {
		"_id": "7140378788918988800",
		"categorie": "Other",
		"name": "video games",
		"official": true,
		"author": {
			"id": "7102956217768611840",
			"username": "punchnox"
		},
		"CreatedAt": "2023-12-12T16:35:40.568Z"
	}
}
```

- Codes d'erreur
    - Code `400 Bad request` : Si le nom du tag ou de la catégorie n'est pas précisé.
    - Code `403 Forbidden` : Si le nom du tag existe déjà.
    - Code `500 Internal Server Error` : Si une erreur inattendue se produit.



## Supprimer un Tag

Permet de supprimer un tag et de le retirer de chaque topics le contenant.
/!\ Indisponible pour les utilisateurs, requête reservé aux membres de rang admin minimum

- **Méthode** : DELETE
- **Endpoint** : `/topic/tag/:id`
- **En-tête (Headers)** :
  - `no content`

### Paramètres du Corps (Body)
- **`name`** (obligatoire) : Le nom du tag.
```json
{
    "name": "name",
}
```

### Réponse en cas de succès

- Code : `200 OK`

- Codes d'erreur
    - Code `400 Bad request` : Si le nom du tag n'est pas précisé.
    - Code `500 Internal Server Error` : Si une erreur inattendue se produit.


## Récupérer les Topics liés à un Tag

Récupère les topics contenant un tag spécifié.

- **Méthode** : GET
- **Endpoint** : `https://ageshistory.com/api/topic/tag/:nom`
- **En-tête (Headers)** :
  - `authorization` : Token JWT de l'utilisateur connecté.

- **Réponse en cas de succès** : Code `200 OK`

tag: art
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