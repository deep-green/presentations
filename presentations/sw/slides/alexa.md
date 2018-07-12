class: center, middle
# Alexa

---

## Technologie
### Alexa

__Programmiersprache:__
- JavaScript

__Framework(s):__
- node.js
- socket.io

---

## Skill
### Alexa

#### Aufrufen des Alexa Skills
__Invocation Name:__
- mein schachspiel

__Beispiel__
- Alexa öffne mein Schachspiel

---

#### Intents

<img src="images/alexa/intents.png" width="50%" />

---

## Code-Snippets
### Alexa

#### Intent im Backend
```js
app.intent('forfeit',
  {
    "slots":{}
	,"utterances":[
    "aufgeben",
		"aufgabe",
		"forfeit",
		"ff",
  ]
  },
  function(request,response) {
		let session = request.getSession();
		let gameid = session.get("gameid");
		return cn.forfeit(gameid).then(function(msg){
	  	response.say("Sie haben aufgegeben.");
			response.shouldEndSession(true);
	});
}
);
```

---

## Code-Snippets
### Alexa

#### Funktion im Backend
```js
exports.forfeit = function (game) {
  return new Promise(function(resolve, reject){
    socket.emit('end', { reason: "lost", ID_game: game, token: tok },
      resolve(""));
  });
}
```

---
