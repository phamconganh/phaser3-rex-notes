## Introduction

Drag game object.

- Author: Rex
- Member of game object

## Source code

[Link](https://github.com/rexrainbow/phaser3-rex-notes/blob/master/plugins/drag-plugin.js)

## Usage

User could import class directly, or install it by global plugin.

### Import class

```javascript
import rexDrag from './plugins/drag.js';
```

### Install global plugin

Install plugin in [configuration of game](game.md#configuration)

```javascript
import DragPlugin from './plugins/drag-plugin.js';

var config = {
    // ...
    plugins: {
        global: [{
            key: 'rexDrag',
            plugin: DragPlugin,
            start: true
        },
        // ...
        ]
    }
    // ...
};
var game = new Phaser.Game(config);
```

### Create instance

```javascript
gameobject.drag = scene.plugins.get('rexDrag').add(gameobject, {
    //enable: true,
    //axis: 0,      //0|'both'|'h&v'|1|'horizontal'|'h'|2|'vertical'|'v'
    //rotation: Phaser.Math.DegToRad(45)  // axis rotation in rad
});
```

Properties

- enable: drag-able
- axis : 
    - `'both'`,`'h&v'`, or `0` : dragging on all directions.
    - `'horizontal'`,`'h'`, or `1` : dragging on horizontal axis.
    - `'vertical'`,`'v'`, or `2` : dragging on vertical axis.
- rotation : axis rotation in rad, available in horizontal or vertical axis mode.

### Dragging events

Built-in dragging events

```javascript
gameobject.on('dragstart', function(pointer, dragX, dragY){ /*...*/ });
gameobject.on('drag', function(pointer, dragX, dragY){ /*...*/ });
gameobject.on('dragend', function(pointer, dragX, dragY, dropped){ /*...*/ });
```

### Get dragging state

```javascript
var isDragging = gameobject.drag.isDragging;
```

### Set rotation of axis

```javascript
gameobject.drag.setAxisRotation(rad);
```

### Set axis mode

```javascript
gameobject.drag.setAxisMode(m);  //0|'both'|'h&v'|1|'horizontal'|'h'|2|'vertical'|'v'
```

### Try drag

Game object will be dragged if there is any point above it.

```javascript
gameobject.drag.drag();
```

### Drop

Game object will be dropped(dragend) manually.

```javascript
gameobject.drag.dragend();
```