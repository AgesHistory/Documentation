# Events

Documentation des endpoints liés aux évenements sur AgesHistory.

# Noel ( calendrier)

## Accéder au calendrier

Permet à un utilisateur d'acceder à l'évenement calendrier de l'avent.

- **Méthode** : GET
- **Endpoint** : `events/2023/noel`

- **Réponse en cas de succès** : `Code 200 OK`
```js
{
	code: 200,
	message: [
		{
			Date: {
				day: 1,
				month: 12
			},
			_id: "id",
			Name: "Anecdotes du 1er Décembre 2023",
			reward: "credits: String...",
			win: 0,
			description: String,//affiche les récompenses passées
			image: String,
			__v: 0
		},
    null,
		null,
		null//null car ce jour là est indisponible...
  ]
}
```


- **Codes d'erreur** :

  - Code `500 Internal Server Error` : Erreur venant du backend.

<br><br>

## Voir un jour du calendrier AgesHistory

Permet de voir les informations de la case du calendrier mentionnée.

- **Méthode** : GET
- **Endpoint** : `events/2023/noel/:day`
- **Réponse en cas de succès** : `Code 200 OK`
```js
{
	code: 200,
	message: {
		Date: {
			day: 1,
			month: 12
		},
		_id: "id",
		Name: "Anecdotes du 1er Décembre 2023",
		reward: String,
		win: 0,
		description: String,
		image: String(url),
		__v: 0
	}
}
```


- **Codes d'erreur** :

  - Code `400 Bad Request` : Si le jour n'est pas précisé.
  - Code `403 Forbidden`: Si la date est incorrecte.
  - Code `500 Internal Server Error` : Si une erreur inattendue se produit.


<br><br>

## Récupérer une récompense

Permet de récupérer une récompense de la case du calendrier mentionnée.

- **Méthode** : GET
- **Endpoint** : `events/2023/noel/reward`
- **Réponse en cas de succès** : `Code 200 OK`
- **En-tête (Headers)** :
  - `Authorization` : Token JWT de l'utilisateur connecté.

```js
{
	code: 200,
	message: {
		Claim: "reward, ex 'credits 50'",
    reward: {
		  Date: {
		  	day: 1,
		  	month: 12
		  },
		  _id: "id",
		  Name: "Anecdotes du 1er Décembre 2023",
		  reward: String,
		  win: 0,
		  description: String,
		  image: String(url),
		  __v: 0
	  },
    user: {
      username: String,
      rewards: [String, String]
    }
	}
}
```


- **Codes d'erreur** :

  - Code `400 Bad Request` : multiples raisons ( dites dans la réponse )
  - Code `401 Unauthorized` : Si l'utilisateur n'est pas connecté ou que son token est invalide.
  - Code `404 not found`: si l'utilisateur n'existe pas.
  - Code `500 Internal Server Error` : Si une erreur inattendue se produit.

## Accéder aux récompenses sur le compte

Permet à un utilisateur d'acceder aux récompenses du gagnés sur le compte

- **Méthode** : GET
- **Endpoint** : `events/2023/noel/@me`
- **En-tête (Headers)** :
  - `Authorization` : Token JWT de l'utilisateur connecté.


- **Réponse en cas de succès** : `Code 200 OK`
```js
{
	"code": 200,
	"message": {
		"_id": "65678b286fa8a5e5a9a8f22b",
		"username": "punchnox",
		"id": "7102956217768611840",
		"rewards": [
			"mystère"
		],
		"__v": 0
	}
}
```


- **Codes d'erreur** :
  - Code `401 Unauthorized` : Si l'utilisateur n'est pas connecté ou que son token est invalide.
  - Code `500 Internal Server Error` : Erreur venant du backend.

<br><br>