# Messagerie privée en temps réel

## Evenement typing

Permet à un utilisateur de montrer au destinataire qu'il est en train d'écrire un message.

- **Données json à envoyer** :

```json
{
    "event": "MESSAGE",
    "action": "typing",
    "data": {
        "to": "id du destinataire",
        "typing": true ou false
    }
}
```
- **Données reçu par le destinataire** :

```json
{
    "event": "MESSAGE",
    "action": "typing",
    "data": {
        "from": "id de l'utilisateur qui est en train d'écrire",
        "typing": true | false
    }
}
```

## Envoie d'un message

Permet à un utilisateur d'envoyer un message en temps réel avec une sauvgarde automatique dans la base de donnée.

- **Données json à envoyer** :

```json
{
    "event": "MESSAGE",
    "action": "message",
    "data": {
        "to": "id de l'utilisateur destinataire",
        "content": "Salut ceci est un message en temps réel"
    }
}
```
- **Données reçu par le destinataire** :

```json
{
    "event": "MESSAGE",
    "action": "message",
    "data": {
        "from": {
            "id": "id de l'auteur",
            "username": "pseudo de l'auteur",
            "avatar": "avatar_url",
            "badges": []
        },
        "message": {
            "id": "id_du_message",
            "content": "Salut ceci est un message en temps réel",
            "createdAt": "timestamp"
        }
    }
}
```

