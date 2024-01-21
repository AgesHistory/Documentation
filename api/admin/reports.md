# Signalements
Documentation des routes administratives concernants les signalements, seuls les utilisateurs ayant les permissions requises auront accès à ces fonctionnalités.

## Afficher les tout les signalements

Récupère tout les signalements et leurs informations.

- **Méthode** : GET
- **Endpoint** : `https://ageshistory.com/api/admin/reports`
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
			"author": {
				"id": 7102951221928923000,
				"username": "Un utilisateur lambda",
				"avatar": "https://ageshistory.com/api/medias/avatar/7103141925003202560.png"
			},
			"_id": "65061a13814065d54979fe54",
			"type": "message",
			"reason": "Spam dans pleins de topics et sur pleins de guilds ( espace communauté )",
			"id": "7103858918018781184",
			"CreatedAt": "2023-09-16T21:11:47.307Z",
			"__v": 0
		}
	]
}
```
- Codes d'erreur
  - Code `401 Unauthorized` : Authorization invalide ou permissions manquantes.
  - Code `500 Internal Server Error` : Si une erreur inattendue se produit.


## Créer un signalement

Fait un signalement à l'adiministration de ageshistory.

- **Méthode** : POST
- **Endpoint** : `https://ageshistory.com/api/admin/reports`
- **En-tête (Headers)** :
  - `authorization`:  Token JWT de l'utilisateur connecté.

### Paramètres du Corps (Body)
```json
{
    "type": "message" | "user" | "topic" | "comment" | "bug",
    "reason": "description du signalement"
}
```

Si le type est message alors il faudra ajouter l'id de l'auteur du message et l'id du message ( de même pour topic, user, comment), donc:
**Message report**
```json
{
    "type": "message",
    "id": "id du message",
    "user": "id de l'auteur du message",
    "reason": "description du signalement"
}
```
**User report**
```json
{
    "type": "user",
    "id": "id de l'utilisateur",
    "reason": "description du signalement"
}
```
**Topic report**
```json
{
    "type": "topic",
    "id": "id du topic",
    "reason": "description du signalement"
}
```
**Comment report**
```json
{
    "type": "comment",
    "id": "id du commentaire",
    "topic": "id du topic",
    "reason": "description du signalement"
}
```
**Comment report**
```json
{
    "type": "bug",
    "reason": "description du signalement lié au bug"
}
```

### Réponse en cas de succès

- Code : `201 Created`

```json
{
	"code": 201,
	"message": {
		"author": {
			"id": 7102956217768612000,
			"username": "punchnox",
			"avatar": "https://ageshistory.com/api/medias/avatar/7102951221928923136.png"
		},
		"type": "bug",
		"reason": "description du signalement lié au bug",
		"id": null,
		"CreatedAt": "2024-01-18T16:27:35.268Z",
		"_id": "65a951771ae25270784453a8",
		"__v": 0
	}
}
```

- Codes d'erreur
  - Code `401 Unauthorized` : Authorization invalide.
  - Code `400 Bad Request` : Si des paramètres du corps (Body) sont manquant.
  - Code `404 Not Found` : Si des informations sont invalides ou inéxistantes.
  - Code `500 Internal Server Error` : Si une erreur inattendue se produit.


## Afficher un signalement mentionné

Affiche les informations d'un signalement en particulier.

- **Méthode** : GET
- **Endpoint** : `https://ageshistory.com/api/admin/reports/:id`
- **En-tête (Headers)** :
  - `authorization`:  Token JWT de l'utilisateur connecté.

### Paramètres du Corps (Body)
`no data`

### Paramètres de l'URL
- `id`: L'identifiant du signalement.

### Réponse en cas de succès

- Code : `200 OK`

```json
{
	"code": 200,
	"message": {
		"author": {
			"id": 7102956217768612000,
			"username": "punchnox",
			"avatar": "https://ageshistory.com/api/medias/avatar/7102951221928923136.png"
		},
		"_id": "65a953601ae25270784453ad",
		"type": "bug",
		"reason": "description du signalement lié au bug",
		"id": null,
		"CreatedAt": "2024-01-18T16:35:44.938Z",
		"__v": 0
	}
}
```
- Codes d'erreur
  - Code `401 Unauthorized` : Authorization invalide ou permissions manquantes.
  - Code `404 Not Found` : Si l'id du signalement n'existe pas.
  - Code `500 Internal Server Error` : Si une erreur inattendue se produit.



## Supprimer un signalement

Supprime un signalement avec l'id fournit dans la requête.

- **Méthode** : DELETE
- **Endpoint** : `https://ageshistory.com/api/admin/reports/:id`
- **En-tête (Headers)** :
  - `authorization`:  Token JWT de l'utilisateur connecté.

### Paramètres du Corps (Body)
`no data`

### Paramètres de l'URL
- `id`: L'identifiant du signalement à supprimer

### Réponse en cas de succès

- Code : `200 OK`

```json
{
	"code": 200,
	"message": "Report deleted"
}
```

- Codes d'erreur
  - Code `401 Unauthorized` : Authorization invalide.
  - Code `404 Not Found` : Si l'id du signalement n'existe pas.
  - Code `500 Internal Server Error` : Si une erreur inattendue se produit.



## Afficher les signalements d'un utilisateur mentionné

Affiche tout les signalements qu'un utilisateur à son encontre.

- **Méthode** : GET
- **Endpoint** : `https://ageshistory.com/api/admin/reports/user/:id`
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
	"message": [
		{
			"author": {
				"id": "71029562174156421564",
				"username": "Un_utilisateur_lambda",
				"avatar": "https://ageshistory.com/api/medias/avatar/7102951221928923136.png"
			},
			"_id": "65a954d7fed03d926a414314",
			"type": "user",
			"reason": "description du signalement lié à du harcèlement venant de cet utilisateur",
			"id": "7102956217748964231",
			"CreatedAt": "2024-01-18T16:41:59.020Z",
			"__v": 0
		}
	]
}
```
- Codes d'erreur
  - Code `401 Unauthorized` : Authorization invalide ou permissions manquantes.
  - Code `404 Not Found` : Si l'id de l'utilisateur n'existe pas.
  - Code `500 Internal Server Error` : Si une erreur inattendue se produit.