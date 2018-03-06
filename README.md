[![Build Status](https://img.shields.io/travis/imba-js/event-emitter.svg?style=flat-square)](https://travis-ci.org/imba-js/event-emitter)

# @imba/event-emitter

Native node.js event emitter with generics for typescript.

## Installation

```bash
$ npm install --save @imba/event-emittter
```

or with yarn

```bash
$ yarn add @imba/event-emitter
```

## Usage

Instead of extending the `EventEmitter` from node.js, create property for each event. It's similar in usage to what 
angular is doing with [rxjs](https://github.com/angular/angular/blob/c6645e7a04a89a992394e19986f9910e42b4b9f0/packages/core/src/event_emitter.ts).

```typescript
import {EventEmitter} from '@imba/event-emitter';

class MyClassWithEvents
{

    public onStart: EventEmitter<string> = new EventEmitter<string>();

    public onFinish: EventEmitter<string> = new EventEmitter<string>();


    public run(): void
    {
        this.onStart.emit('started');
        this.onFinish.emit('finished');
    }

}

const instance = new MyClassWithEvents;

instance.onStart.subscribe((msg) => {
    console.log(msg);    // output: started
});

instance.onFinish.subscribe((msg) => {
    console.log(msg);    // output: finished
});

instance.run();
```
