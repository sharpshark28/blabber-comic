# Blabber-Comic

## Sample

![Preview](/comic.png)

## How it works

Powered by Node and a node-canvas a comic can automatically be generated from a json array of users/text and some characters/backgrounds to be chosen at random.

## How to use it

### Generate base64Data

```javascript
const blabbercomic = require('blabber-comic');
let messages = [] // Array of messages...

blabbercomic(messages).then(response => {
  console.log('Generated comic as base64 data', response);
}).catch(error => {
  throw error;
});
```

### Save as file with `fs`

Example included in project. Clone then run `npm run test`.

```javascript
const blabbercomic = require('blabber-comic');
const fs = require('fs');
let messages = [] // Array of messages...

blabbercomic(messages).then(response => {
  let base64Data = response.replace(/^data:image\/png;base64,/, '');

  fs.writeFile('./storage/comics/comic.png', base64Data, 'base64', error => {
    if (error) console.error('Uhoh...', error);
    else console.log('Saved file as `comic.png`');
  });
}).catch(error => {
  throw error;
});
```

### Customizing characters and backgrounds

```javascript
const blabbercomic = require('blabber-comic');
let backgrounds = ['./assets/backgrounds/1.png', './assets/backgrounds/2.png'];
let characters = ['./assets/characters/1.png', './assets/characters/2.png', './assets/characters/3.png']; // Provide at least 3
let comicSize = 400; // in px square

let messages = [] // Array of messages...
let config = { backgrounds, characters, comicSize };

blabbercomic(messages, config);
```

---

## Special thanks to:

* [node-canvas](https://github.com/Automattic/node-canvas) by Cairo
* avatars by Iulia Ardeleanu from the Noun Project
* backgrounds by Olga Libby from Subtle Patterns