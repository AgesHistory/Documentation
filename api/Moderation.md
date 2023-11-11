# Authentification

Documentation des endpoints liés à la modération du forum

## Register

Permet à un utilisateur de signaler un message, un utilisateur, un commentaire ou un topic.

- **Méthode** : POST
- **Endpoint** : `admin/report/`
- **Paramètres du corps (Body)** :

```js
{
    "type": "message",
    "id": 1,
    "user": "id", || "topic": "id",
    "reason": "Spam"
}
```
- **Réponse en cas de succès** : `Code 201 Created`
```json
{
    "token": "eyjh69ZD2G0bw2389HD0vNF9WZddz28.eyjh69ZP20CxDBmfD2G0bw2389HDP20CxDBmf0vNF9WZddz28.egfSdsHJHhHPMQAaeQn_389HDP_89HD0vqNF9WdDda_g"
}
```


- **Codes d'erreur** :

  - Code `400 Bad Request` : Si les données fournies sont incorrectes. (type, reason, id, manquant par exemple)
  - Code `401 Unauthorized` : Si l'utilisateur n'est pas connecté.	
  - Code `404 No Found` : Si le message, l'utilisateur, le commentaire ou le topic n'existe pas.