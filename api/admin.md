# Admin
Documentation des routes administratives, seuls les utilisateurs ayant les permissions requises auront accès à ces fonctionnalités.

## Afficher les tout utilisateurs bannis

Récupère tout les bannissements avec leurs informations.

- **Méthode** : GET
- **Endpoint** : `https://ageshistory.com/api/admin/users/banned`
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
			"user": {
				"id": 7103141925003203000,
				"username": "bob",
				"avatar": "https://ageshistory.com/api/medias/avatar/7103141925003202560.png"
			},
			"_id": "65a7c27f06603fafccaa583e",
			"id": 7103141925003203000,
			"reason": "Raison du bannissement.",
			"admin": "punchnox",
			"CreatedAt": "2024-01-16T18:19:17.177Z",
			"__v": 0
		}
	]
}
```

- Codes d'erreur
    - Code `500 Internal Server Error` : Si une erreur inattendue se produit.