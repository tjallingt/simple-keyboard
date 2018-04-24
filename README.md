# simple-keyboard

[![npm](https://img.shields.io/npm/v/simple-keyboard.svg)](https://www.npmjs.com/package/simple-keyboard)

<a href="https://franciscohodge.com/projects/simple-keyboard/"><img src="src/demo/images/simple-keyboard.png" align="center"></a>
> An easily customisable and responsive on-screen virtual keyboard for Javascript projects.

> Want the React.js version? Get [react-simple-keyboard](https://www.npmjs.com/package/react-simple-keyboard) instead!

<img src="src/demo/images/keyboard.PNG" align="center" width="100%">

<b>[Live Demo](https://franciscohodge.com/simple-keyboard/demo)</b>


## Installation

### npm

`npm install simple-keyboard --save`

### zip file (self-hosted)

[Click here to download the latest release (zip format).](https://github.com/hodgef/simple-keyboard/zipball/master)

> Want to use a CDN instead of self-host? Scroll down to the "Usage from CDN" instructions below.

## Usage with npm

### js

````js
import Keyboard from 'simple-keyboard';
import 'simple-keyboard/build/css/index.css';

class App {
  constructor(){
    document.addEventListener('DOMContentLoaded', this.onDOMLoaded);
  }

  onDOMLoaded = () => {
    this.keyboard = new Keyboard({
      onChange: input => this.onChange(input),
      onKeyPress: button => this.onKeyPress(button)
    });
  }

  onChange = input => {
    console.log("Input changed", input);
  }

  onKeyPress = button => {
    console.log("Button pressed", button);
  }
}

export default App;
````

### html

````html
<div class="simple-keyboard"></div>
````

> Need a more extensive example? [Click here](https://github.com/hodgef/simple-keyboard/blob/master/src/demo/App.js).

## Usage from CDN

### html

````html
<!DOCTYPE html>
<html lang="en">
<head>
    <link rel="stylesheet" href="https://cdn.rawgit.com/hodgef/simple-keyboard/d477c35c/build/css/index.css">
</head>
<body>
    <div class="simple-keyboard"></div>
    <script src="https://cdn.rawgit.com/hodgef/simple-keyboard/d477c35c/build/index.js"></script>
    <script>
      function keyboard_onChange(input){
        console.log("Input chanfed", input);
      }

      function keyboard_onKeyPress(button){
        console.log("Button pressed", button);
      }

      var myKeyboard = new Keyboard({
        onChange: input => keyboard_onChange(input),
        onKeyPress: button => keyboard_onKeyPress(button)
      });
    </script>
</body>
</html>
````

## Options

You can customize the Keyboard by passing options to it.
Here are the available options (the code examples are the defaults):

### layout

> Modify the keyboard layout

```js
layout: {
  'default': [
    '` 1 2 3 4 5 6 7 8 9 0 - = {bksp}',
    '{tab} q w e r t y u i o p [ ] \\',
    '{lock} a s d f g h j k l ; \' {enter}',
    '{shift} z x c v b n m , . / {shift}',
    '.com @ {space}'
  ],
  'shift': [
    '~ ! @ # $ % ^ & * ( ) _ + {bksp}',
    '{tab} Q W E R T Y U I O P { } |',
    '{lock} A S D F G H J K L : " {enter}',
    '{shift} Z X C V B N M < > ? {shift}',
    '.com @ {space}'
  ]
}
```

### layoutName

> Specifies which layout should be used.

```js
layoutName: "default"
```

### display

> Replaces variable buttons (such as `{bksp}`) with a human-friendly name (e.g.: "delete").

```js
display: {
  '{bksp}': 'delete',
  '{enter}': '< enter',
  '{shift}': 'shift',
  '{s}': 'shift',
  '{tab}': 'tab',
  '{lock}': 'caps',
  '{accept}': 'Submit',
  '{space}': ' ',
  '{//}': ' '
}
```

### theme

> A prop to add your own css classes. You can add multiple classes separated by a space.

```js
theme: "hg-theme-default"
```

### debug

> Runs a console.log every time a key is pressed. Displays the buttons pressed and the current input.

```js
debug: false
```

### newLineOnEnter

> Specifies whether clicking the "ENTER" button will input a newline (`\n`) or not.

```js
newLineOnEnter: false
```

## Methods

simple-keyboard has a few methods you can use to further control it's behavior.
To access these functions, you need the instance the simple-keyboard component, like so:

```js
var keyboard = new Keyboard({
  ...
});
/>

// Then, use as follows...
keyboard.methodName(params);
```

### clearInput

> Clear the keyboard's input.

```js
keyboard.clearInput();
```

### getInput

> Get the keyboard's input (You can also get it from the _onChange_ prop).

```js
let input = keyboard.getInput();
```

### setInput

> Set the keyboard's input. Useful if you want the keybord to initialize with a default value, for example.

```js
keyboard.setInput("Hello World!");
```

## Demo

<img src="src/demo/images/demo.gif" align="center" width="600">

### Live demo

[https://franciscohodge.com/simple-keyboard/demo](https://franciscohodge.com/simple-keyboard/demo)

### To run demo on your own computer

* Clone this repository
* `npm install`
* `npm start`
* Visit [http://localhost:3000/](http://localhost:3000/)

## Note

This is a work in progress. Feel free to submit any issues you have at:
[https://github.com/hodgef/simple-keyboard/issues](https://github.com/hodgef/simple-keyboard/issues)
