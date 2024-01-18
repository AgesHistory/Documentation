# Follow

Documentation des endpoints liés aux abonnements ( utilisateur et topic )

## Obtention de la liste des abonnements

Récupère la liste des utilisateurs suivis et en attente de d'abonnement.

- **Méthode** : GET
- **Endpoint** : `/identity/@me/follow`
- **En-tête (Headers)** :
  - `authorization` : Token JWT de l'utilisateur connecté.

- **Réponse en cas de succès** : Code `200 OK`

```json
{
	"code": 200,
	"message": {
		"follow_request": ["id1", "id2"],
		"following": ["id1", "id2"]
	}
}
```
- **Codes d'erreur** :
  - Code `401 Unauthorized` : Si l'utilisateur n'est pas authentifié.


## S'abonne à un utilisateur

Ajoute ou envoie une demande d'abonnement à l'utilisateur cible.

- **Méthode** : POST
- **Endpoint** : `/identity/@me/follow/:id`
- **En-tête (Headers)** :
  - `authorization` : Token JWT de l'utilisateur connecté.

- **Réponse en cas de succès** : Code `200 OK`

/!\ Si le compte de l'utilisateur est privé une demande d'abonnement sera envoyé autrement l'abonnement se fera automatiquement.

```json
{
	"code": 200,
	"message": "ok"
}
```
- **Codes d'erreur** :
  - Code `404 Not Found` : Si l'utilisateur n'est pas trouvé.

## Se désabonner d'un utilisateur

Supprime l'abonnement à un utilisateur.

- **Méthode** : DELETE
- **Endpoint** : `/identity/@me/follow/:id`
- **En-tête (Headers)** :
  - `authorization` : Token JWT de l'utilisateur connecté.

- **Réponse en cas de succès** : Code `200 OK`


```json
{
	"code": 200,
	"message": "ok"
}
```
- **Codes d'erreur** :
  - Code `404 Not Found` : Si l'utilisateur n'existe pas, si l'utilisateur n'a psa été trouvé dans la liste d'abonnements, ou si l'utilisateur n'a pas été trouvé dans la liste de demandes d'abonnements
