class: center, middle
# Frontend
## Alexa

---

## Technologie
### Frontend - Alexa

__Programmiersprache:__
- JavaScript

__Framework(s):__
- node.js
- socket.io

---

## Skill
### Frontend - Alexa

#### Aufrufen des Alexa Skills
__Invocation Name:__
- mein schachspiel

__Beispiel__
- Alexa öffne mein Schachspiel

---

## Intents
### Frotend - Alexa

__Intents:__
- newGame - Erstellt neues Spiel
- makeMove - Zug machen, auf Zug warten
- whoseTurn - Wer ist am Zug
- lastTurn - Letzter Zug des Gegners
- forfeit - Aufgabe

---

## Code-Snippets
### Frotend - Alexa

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
### Frotend - Alexa

#### Funktion im Backend
```js
exports.forfeit = function (game) {
  return new Promise(function(resolve, reject){
    socket.emit('end', { reason: "lost", ID_game: game, token: tok },
      resolve(""));
  });
}
```
