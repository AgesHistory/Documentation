# Permissions
#### Documentation des routes administratives concernants les permissions, seuls les utilisateurs ayant la permission "MANAGE_ROLES" requises auront accès à ces fonctionnalités.

---
Les permissions sont classées par grades et peuvent être ajoutées indépendamment des rôles.
```json
# Les Permissions et leurs rôles
{
  "MODERATION": {
    "BAN": 8,
    "BAN_IP": 16,
    "MUTE": 32,
    "WARNINGS": 64,
    "STAFF_PRIVATE_ACCESS": 128,
    "REPORT_NOTIFICATIONS": 256,
    "UNBAN": 512,
    "VIEW_BAN": 1024
  },
  "ADMINISTRATION": {
    "MANAGE_PROFILES": 2048,
    "MANAGE_ROLES": 4096,
    "MANAGE_TICKETS": 8192,
    "MANAGE_USER_ACCOUNTS": 16384,
    "ADMIN_NOTIFICATIONS": 32768,
    "MANAGE_MESSAGES": 65536
  },
  "FORUMS_THREADS": {
    "CREATE_FORUM": 131072,
    "DELETE_FORUM": 262144,
    "LOCK_FORUM": 524288,
    "UNLOCK_FORUM": 1048576,
    "CHANGE_OWNER": 2097152,
    "PIN_UNPIN": 4194304,
    "ARCHIVE_FORUM": 8388608,
    "CREATE_DELETE_MODIFY_THREADS": 16777216
  },
  "GAMING": {
    "CREATE_GAME": 33554432,
    "DELETE_GAME": 67108864,
    "CREATE_ANIMATION": 134217728,
    "DELETE_ANIMATION": 268435456
  }
}

```

---

## Voir les permissions accordées à un utilisateur

Affiche les permissions de l'utilisateur mentionné sous forme de tableaux de valeurs ( Array )

- **Méthode** : GET
- **Endpoint** : `https://ageshistory.com/api/admin/users/permissions/:id de l'utilisateur`
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
		"BAN",
		"BAN_IP",
		"WARNINGS",
		"UNBAN",
		"VIEW_BAN",
		"MANAGE_ROLES",
		"MANAGE_MESSAGES",
		"LOCK_FORUM",
		"CREATE_DELETE_MODIFY_THREADS"
	]
}
```

- Codes d'erreur
  - Code `401 Unauthorized` : Authorization invalide ou permissions `MANAGE_ROLES` manquante.
  - Code `500 Internal Server Error` : Si une erreur inattendue se produit.

---

## Ajouter une permission à un utilisateur

Permet d'ajouter des permissions à l'utilisateur de vôtre choix.
**/!\ Nécessite la permission `MANAGE_ROLES`**

- **Méthode** : POST
- **Endpoint** : `https://ageshistory.com/api/admin/users/permissions/:id de l'utilisateur`
- **En-tête (Headers)** :
  - `authorization`:  Token JWT de l'utilisateur connecté.

### Paramètres du Corps (Body)
```json
# Exemples de permissions à ajouter
# La liste de permissions se trouve ci dessus
{
    "permissions": [
        "BAN",
        "BAN_IP"
    ]
}
```


### Réponse en cas de succès

- Code : `200 OK`

```json
{
	"code": 200,
	"message": {
		"list": [
			"BAN",
			"BAN_IP"
		],
		"value": 24
	}
}
```

- Codes d'erreur
  - Code `401 Unauthorized` : Authorization invalide ou permissions `MANAGE_ROLES` manquante.
  - Code `400 Bad Request` : Si des paramètres du corps (Body) sont manquant ou incorrect.
  - Code `500 Internal Server Error` : Si une erreur inattendue se produit.

---

## Supprimer une permission à un utilisateur

Permet de supprimer des permissions à l'utilisateur de vôtre choix.
**/!\ Nécessite la permission `MANAGE_ROLES`**

- **Méthode** : DELETE
- **Endpoint** : `https://ageshistory.com/api/admin/users/permissions/:id de l'utilisateur`
- **En-tête (Headers)** :
  - `authorization`:  Token JWT de l'utilisateur connecté.

### Paramètres du Corps (Body)
```json
# Exemples de permissions à supprimer
# La liste de permissions se trouve ci dessus
{
    "permissions": ["BAN"]
}
```


### Réponse en cas de succès

- Code : `200 OK`

```json
{
	"code": 200,
	"message": {
		"permissions": ["BAN_IP"],
		"permissions_code": 16
	}
}
```

- Codes d'erreur
  - Code `401 Unauthorized` : Authorization invalide ou permissions `MANAGE_ROLES` manquante.
  - Code `400 Bad Request` : Si des paramètres du corps (Body) sont manquant ou incorrect.
  - Code `500 Internal Server Error` : Si une erreur inattendue se produit.
