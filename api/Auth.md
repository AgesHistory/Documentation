# Authentification

Documentation des endpoints liés à l'authentification des utilisateurs.

## Register

Permet à un utilisateur de s'inscrire.

- **Méthode** : POST
- **Endpoint** : `identity/auth/register`
- **Paramètres du corps (Body)** :

```json
{
    "username": "john_doe",
    "email": "john@example.com",
    "password": "secretpassword"
}
```
- **Réponse en cas de succès** : `Code 201 Created`
```json
{
    "token": "eyjh69ZD2G0bw2389HD0vNF9WZddz28.eyjh69ZP20CxDBmfD2G0bw2389HDP20CxDBmf0vNF9WZddz28.egfSdsHJHhHPMQAaeQn_389HDP_89HD0vqNF9WdDda_g"
}
```


- **Codes d'erreur** :

  - Code `400 Bad Request` : Si les données fournies sont incorrectes.
  - Code `409 Conflict` : Si l'utilisateur existe déjà.

<br><br>
## Login

Permet à un utilisateur de se connecter.

- **Méthode** : POST
- **Endpoint** : `identity/auth/login`
- **Paramètres du corps (Body)** :

```json
{
  "email": "john@example.com",
  "password": "secretpassword"
}
```
- **Réponse en cas de succès** : `Code 200 OK`
```json
{
    "token": "eyjh69ZD2G0bw2389HD0vNF9WZddz28.eyjh69ZP20CxDBmfD2G0bw2389HDP20CxDBmf0vNF9WZddz28.egfSdsHJHhHPMQAaeQn_389HDP_89HD0vqNF9WdDda_g"
}
```


- **Codes d'erreur** :

  - Code `400 Bad Request` : Si les données fournies sont incorrectes.
  - Code `401 Conflict` : Si les informations de connexion sont incorrectes.
  - Code `403 Forbidden`: Si l'email ou le mot de passe est invalid.
  - Code `409 Conflit`: Si l'email ou le nom d'utilisateur est déjà associé à un compte.
  - Code `500 Internal Server Error` : Si une erreur inattendue se produit.