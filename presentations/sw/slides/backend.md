class: center, middle
# Backend

---

## Technologie
### Backend / Zuggenerator

__Programmiersprache(n):__
- JavaScript
- Rust

__Framework(s):__
- node.js
- neon-bindings
- mongoose
- Jest
- socket.io
- JSDoc

---

## Code-Snippets
### Backend
#### Verbindung und Nutzung der KI

```javascript
//socket client for AI 1 (tensorflow)
const socketAi1 = require('socket.io-client')('http://ec2-54-93-171-91.eu-central-1.compute.amazonaws.com:8008');

socketAi1.on('makeMove', (data) => {

    db_connector.ActiveGameData.findById(data.ID_game, 'socketRoom', (err, game)=> {
        if(err || (game.socketRoom === undefined)) {
            socketAi1.emit('reject', dg_interface.emit_reject());
            return;
        }

        //send 'receive' to other player and all viewers watching the game
        io.of('/').in(game.socketRoom).emit('receive', dg_interface.emit_receive(data.FEN, data.ID_game, false));

    });
});
```

---

## Code-Snippets
### Backend
#### Verwaltung von Verbindungen

```javascript
//helper function - setting of user token if it still is null
function setUserTokenIfNull(socketId, jwtToken) {
    if(activeConnections[socketId] == null) {
        activeConnections[socketId] = jwtToken;
    }
}

// socket server events 
io.on('connection', (client) => {

    //add new connection to activeConnections
    activeConnections[client.id] = null;

    // disconnect -> remove client from list
    client.on('disconnect', ()=> {
        delete activeConnections[client.id];
    });
    .
    .
    .
```
---

## Code-Snippets
### Backend
#### Verwaltung von Verbindungen

```javascript
//client wants to create new game
    client.on('newGame', (data) => {
        if(dg_interface.check_newGame(data) === true) {
            setUserTokenIfNull(client.id, data.token);
            .
            .
            .
```
---

## Code-Snippets
### Backend
#### Nutzung der Datenbank zur Verwaltung der Spiele

```javascript
db_connector.ActiveGameData.findById(data.ID_game, 'socketRoom whiteID blackID', (err, game)=> {

    if(err || (game.socketRoom === undefined)) {
        client.emit('reject', dg_interface.emit_reject());
        return;
    }

    let sendData = dg_interface.emit_receive(data.FEN, data.ID_game, false); 

    //send 'receive' to other player and all viewers watching the game
    client.to(game.socketRoom).emit('receive', sendData);
    client.emit('receive', sendData);

    if(game.whiteID === 'ki_1' || game.blackID === 'ki_1') {
        socketAi1.emit('receive', sendData);
    } else if (game.whiteID === 'ki_2' || game.blackID === 'ki_2') {
        socketAi2.emit('receive', sendData);
    }

});
```

---

## Code-Snippets
### Backend
#### `dg_interface.emit_` Funktionen zur Generierung von Event-Daten nach Protokoll-Spezifikation

```javascript
function emit_receive(fen, id_game, color) {

    if (id_game <= 0) {
        return undefined;
    }

    let data = {
        FEN: fen,
        ID_game: id_game,
        color: color,
        turns: []
    };

    if((data.FEN === undefined) || (data.FEN === "") || (data.FEN.length == 4)) {
        data.FEN = "rnbqkbnr/pppppppp/8/8/8/8/PPPPPPPP/RNBQKBNR w KQkq - 0 1"
    }

    data.turns = moveGenerator.getMoves(data.FEN).split(", ");

    return data;
}
```

---

## Code-Snippets
### Backend
#### `dg_interface.check_` Funktionen zur Überprüfung der Wohlgeformtheit von Event-Daten

```javascript
function check_makeMove(data) {
    let retVal = true;

    if (typeof (data) !== 'object') {
        retVal = false;
    } else {
        if (!data.hasOwnProperty('FEN')) {
            retVal = false;
        }

        if (!data.hasOwnProperty('ID_game')) {
            retVal = false;
        }

        if (!data.hasOwnProperty('token')) {
            retVal = false;
        }
    }

    return retVal;
}
```

---

## Code-Snippets
### Backend
#### `dg_imageRecognition.getFEN` Funktion zur Nutzung der Bilderkennung

```javascript
function getFEN(buffer, pyModulePath) {
    return new Promise((resolve, reject) => {
        let resultFEN = '';
        let ImageReader = require('child_process').spawn('python3.6', [pyModulePath]);

        // send buffer to input stream and close input stream
        ImageReader.stdin.write(buffer);
        ImageReader.stdin.end();

        // append chunk of data to result FEN if a chunk occurs on stdout
        ImageReader.stdout.on('data', (chunk) => {
            resultFEN = resultFEN + chunk;
        });

        .
        .
        .
```

---

## Code-Snippets
### Backend
#### `dg_imageRecognition.getFEN` Funktion zur Nutzung der Bilderkennung

```javascript
        .
        .
        .
        // RESOLVE if stdout stream is read completely
        ImageReader.stdout.on('end', () => {
            resolve(String(resultFEN));
        });

        //REJECT promise and KILL ImageReader to safely terminate process
        ImageReader.stderr.on('data', (data) => {
            ImageReader.kill('SIGKILL');
            reject(data);
        });

        //watch for process to exit 
        ImageReader.on('exit', () => {
            reject('process terminated without returning FEN')
        });
    });
}
```