# Tags
Les tags vous permettent de trouver des topics plus facilement, les ordonner dans de catégories bien distinctes et de repérer un topic venant d'une catégorie officiel et non-officiel.

## Afficher tout les tags

Récupère tout les tags et leurs spécificités.

- **Méthode** : GET
- **Endpoint** : `/topic/tag`
- **En-tête (Headers)** :
  - `Authorization` : Token JWT de l'utilisateur connecté.

## Paramètres du Corps (Body)

- **`name`** : Le nom du topic (facultatif).
- **`description`** : La description du topic (facultatif).
- **`content`** : Le contenu du topic (facultatif).
- **`tags`** : Les tags du topic (facultatif).

## Réponse en cas de succès

- Code : `200 OK`

```json
{
    "code": 200,
    "message": {
        "_id": "ID_du_topic",
        "name": "Nom_du_topic",
        "description": "Description_du_topic",
        "content": "Contenu_du_topic",
        "likes": [],
        "dislikes": [],
        "share": [],
        "views": "Nombre_de_vues_du_topic ( Number )",
        "edited": "Boolean",
        "comments": [
            "ID_du_commentaire",
            "ID_du_commentaire2"
        ],
        "owner": 7101254393973969000,
        "createdAt": "2023-08-29T21:49:28.438Z"
    }
}
```

- Codes d'erreur

    - Code `400 Bad Request` : Si le nom du topic n'est pas spécifié.
    - Code `401 Unauthorized` : Si l'utilisateur n'est pas authentifié.
    - Code `404 Not Found` : Si le topic n'est pas trouvé.
    - Code `500 Internal Server Error` : Si une erreur inattendue se produit.

    