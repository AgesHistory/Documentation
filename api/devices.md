# Settings

Documentation des endpoints liés aux paramètres utilisateurs.

## Obtention des appareils connectés/Ip blacklist.

Récupère la liste de tout les appareils connectés au compte de l'utilisateur et des adresses ip dans la liste noire.

- **Méthode** : GET
- **Endpoint** : `/identity/@me/devices`
- **En-tête (Headers)** :
  - `Authorization` : Token JWT de l'utilisateur connecté.

### Paramètres du Corps (Body)
`no data`

### Réponse en cas de succès
- Code `200 OK`
- 
```json
{
	"code": 200,
	"message": {
		"_id": "7139585888291393536",
		"devices": [
			{
				"ip": "192.168.1.1",//ip public
				"browser": "Chrome",
				"browserVersion": "112.0.0.0",
				"os": "Android",
				"osVersion": "13",
				"deviceType": "Mobile",
				"CreatedAt": "2023-12-10T12:05:23.260Z",
				"_id": "6575a983ca40f7e782166469"
			}
		],
		"blacklist": [
			"192.168.1.2"
		]
	}
}
```
- **Codes d'erreur** :
  - Code `401 Unauthorized` : Si l'utilisateur n'est pas authentifié.

## Blacklist IP.

Vous avez la possibilité d'ajouter des adresses Ip dans la liste noire de votre compte rendant l'accès à votre compte impossible celles-ci

- **Méthode** : POST
- **Endpoint** : `/identity/@me/devices/blacklist`
- **En-tête (Headers)** :
  - `Authorization` : Token JWT de l'utilisateur connecté.

### Paramètres du Corps (Body)

```json
{
	"ip": "192.168.1.1"
}
```

### Réponse en cas de succès
- Code `200 OK`

```json
{
	"code": 200,
	"message": "IP added to blacklist."
}
```
- **Codes d'erreur** :
  - Code `401 Unauthorized` : Si l'utilisateur n'est pas authentifié.


## Unblacklist IP.

Retire l'adresse ip mentionné dans la requête de la liste noire.

- **Méthode** : DELETE
- **Endpoint** : `/identity/@me/devices/blacklist`
- **En-tête (Headers)** :
  - `Authorization` : Token JWT de l'utilisateur connecté.

### Paramètres du Corps (Body)

```json
{
	"ip": "192.168.1.1"
}
```

### Réponse en cas de succès
- Code `200 OK`

```json
{
	"code": 200,
	"message": "IP removed from blacklist."
}
```
- **Codes d'erreur** :
  - Code `401 Unauthorized` : Si l'utilisateur n'est pas authentifié.
