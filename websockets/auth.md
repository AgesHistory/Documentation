# Authentification

Documentation des requetes pour s'authentifier au serveur websockets

## Connexion

Permet à un utilisateur de s'authentifier pour envoyer et recevoir des données. ( Authentification nécessaire lors de la première connexion, les données pourront être ensuite envoyés sur la requete websocket )

- **Méthode** : Websockets
- **url** : `ws://localhot:4000/`
- **En-tête (Headers)** :

```json
{
    "authorization": "token"
}
```
    ou
- **Params** : `ws://localhost:4000/?authorization=token`
  
- **Réponse en cas de succès** : `Code 101 Switching Protocols`
```json
{
	"event": "CONNECTED",
	"data": {
		"id": "user_id",
		"username": "username",
		"avatar": "avatar_url"
	}
}
```


- **Codes d'erreur** :

  - `401 Unauthorized` : L'utilisateur n'est pas authentifié