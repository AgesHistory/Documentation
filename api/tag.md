# Tags
Les tags vous permettent de trouver des topics plus facilement, les ordonner dans de catégories bien distinctes et de repérer un topic venant d'une catégorie officiel et non-officiel.


## Afficher tout les tags

Récupère tout les tags et leurs spécificités.

- **Méthode** : GET
- **Endpoint** : `/topic/tag`
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
			"author": {
				"id": "7103141925003202560",
				"username": "bob"
			},
			"_id": "7125155703517351936",
			"name": "History",
			"official": true,
			"CreatedAt": "2023-10-31T16:24:55.583Z"
		},
		{
			"author": {
				"id": "7103141925003202560",
				"username": "bob"
			},
			"_id": "7125156076760076288",
			"name": "art",
			"official": true,
			"CreatedAt": "2023-10-31T16:26:15.164Z"
		}
	]
}
```

- Codes d'erreur
    - Code `500 Internal Server Error` : Si une erreur inattendue se produit.

    

## Créer un tag

Vous permet de créer un tag et le proposer à toute la communauté.

- **Méthode** : POST
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

- Code : `201 Created`

```json
{
	"code": 201,
	"message": {
		"_id": "7132058651157598208",
		"name": "My First Tag",
		"official": true,
		"author": {
			"id": "7102951221928923136",
			"username": "salut"
		},
		"CreatedAt": "2023-11-19T17:32:49.867Z"
	}
}
```

- Codes d'erreur
    - Code `400 Bad request` : Si le nom du tag n'est pas précisé.
    - Code `403 Forbidden` : Si le nom du tag existe déjà.
    - Code `500 Internal Server Error` : Si une erreur inattendue se produit.



## Supprimer un Tag

Permet de supprimer un tag et de le retirer de chaque topics le contenant.
/!\ Indisponible pour les utilisateurs, requête reservé aux membres de rang 3 minimum

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
- **Endpoint** : `/topic/tag/:tag`
- **En-tête (Headers)** :
  - `Authorization` : Token JWT de l'utilisateur connecté.

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