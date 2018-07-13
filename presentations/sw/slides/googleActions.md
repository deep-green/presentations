class: center, middle

# Frontend
## Google Actions

---

## Technologie
### Frontend - Google Actions

__Programmiersprache(n):__
- JavaScript

__Framework(s):__
- node.js

__Weiteres:__
- JSON Dateiformat
- gactions CLI

---

## How to
### Frontend - Google Actions

__Google Actions erstellen__
- Dialogflow
- Template
- Google Actions SDK

__Bereitstellen__
- Fulfillment

---

## How to
### Frontend - Google Actions

<img src="images/dialogflowui.png" width="70%" />

---

## How to
### Frontend - Google Actions / Google Actions SDK

__Wissenswertes__
- Google Actions funktionieren über Google Account

__Projekt erstellen__
- gactions CLI herunterladen
- Projekt initiieren ("gactions init")
- erstellt: action.json

__Actions updaten__
- lokale Dateien hochladen
- gactions update --action_package PACKAGE_NAME --project PROJECT_NAME
- gactions update --action_package action.json --project hope-6fc92

---

## How to
### Frontend - Google Actions / Google Actions SDK
#### action.json

```json
{
  "actions": [
    {
      "description": "Default Welcome Intent",
      "name": "MAIN",
      "fulfillment": { "conversationName": "deepgreen" },
      "intent": {
        "name": "actions.intent.MAIN",
        "trigger": {
          "queryPatterns": [ "schach spielen" ]
        }
      }
    }
  ],
  "conversations": {
    "deepgreen": {
      "name": "deepgreen",
      "url": "https://pensive-updike.bespoken.link/",
      "fulfillmentApiVersion": 2
    }
  },
  "locale": "de"
}
```

---

## How to
### Frontend - Google Actions / Google Actions SDK
#### Fulfillment

```js
'use strict';

const {actionssdk} = require('actions-on-google');
const functions = require('firebase-functions');
const socket = require('socket.io-client')('http://ec2-54-93-171-91.eu-central-1.compute.amazonaws.com:4999');
const app = actionssdk({debug: true});

app.intent('actions.intent.MAIN', (conv) => {
  conv.ask('Willkommen in deep green! Was möchten Sie tun?');
});

app.intent('actions.intent.NEWGAME', (conv) => {
  socket.emit('newGame', { ... },

  socket.once('receive', function(msg) {
    conv.ask('Es wird ein neues Spiel gestartet.')
  });

  socket.once('reject', function() {
    conv.ask('Es konnte kein neues Spiel gestartet werden.')
  });
})
exports.myFunction = functions.https.onRequest(app);
```