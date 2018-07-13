class: center, middle
# Datenbank

---

## Technologie
### Datenbank

__DBMS:__
- mongoDB

__Bibliothek(en):__
- mongoose

---

## ER Diagramm
### Backend

<center><img src="images/deepGreen_ER_diag.png" width="90%" /></center>

---

## Code-Snippets
### Backend
#### Objekt-Abbildung der User Daten

```javascript
let userDataSchema = new mongoose.Schema({
  _id: { type: Schema.Types.ObjectId, required: true },
  username: String,
  password: String,
  elo: Number,
  token: String
},
  { collection: 'user' }
);

userDataSchema.methods.calcElo = (enemyElo, result) => {
  if (enemyElo === Number) {
    let exp = (enemyElo - this.elo) / 400;
    let median = 1 / (1 + Math.pow(10, exp));

    this.elo = this.elo + (10 * (result - median));
  }

  return this.elo;
};
```

---

## Code-Snippets
### Backend
#### Objekt-Abbildung der gesicherten Spiele

```javascript
let gameDataSchema = new mongoose.Schema({
  _id: { type: Schema.Types.ObjectId, required: true },
  fen: [String],
  whiteID: String,
  blackID: String,
  winner: String
},
  { collection: 'games' }
);
```

---

## Code-Snippets
### Backend
#### Objekt-Abbildung der aktiven Spiele

```javascript
let activeGameDataSchema = new mongoose.Schema({
  _id: { type: Schema.Types.ObjectId, required: true },
  whiteID: String,
  blackID: String,
  viewers: [String],
  socketRoom: String
},
  { collection: 'activeGames' }
);
```