# MIDI.js - a tiny helper around the WebMIDI API

MIDI.js is a tiny library providing some help to kick-start WebMIDI-enabled projects. See it in action on this [example page](https://github.com/boblemarin/MIDI.js).

## Features

- Auto-populates select controls with available MIDI inputs and outputs
- Handles single input/output selection
- Remembers last chosen inputs/outputs and automatically re-selects them
- Offers simple functions for sending MIDI messages (noteon, noteoff, cc)
- Allows to set a callback function called when incoming MIDI messages are received


## How to use


### Installation
Link your HTML page to the MIDI.js file

```
<script src="path/to/MIDI.js"></script>
```

### Inputs
To allow input selection, simply add the following code to your HTML page, MIDI.js will automatically find the element in the page and populate it with available MIDI inputs. 

```
<select id="midi-input-select"></select>
```


### Outputs
To allow output selection, add this code to your HTML page, MIDI.js will populate it with available MIDI outputs. 

```
<select id="midi-output-select"></select>
```

### Sending MIDI messages

MIDI.js exposes three simples methods to send MIDI messages :

```
MIDI.noteOn( channel, note, velocity )
MIDI.noteOff( channel, note )
MIDI.cc( channel, cc, value )
```
Example : 

``` 
// playing a C2 note on channel 1
MIDI.noteOn( 1, 48, 100 );
```

### Sending custom messages

If you need to send a more specific MIDI message, the ```sendBytes```method gives you the total control by accepting an array of bytes. This method does not check the sent values for validity.

```
let bytes = [ 144, 60, 100 ];
MIDI.sendBytes( bytes );
```

### Receiving MIDI messages

In order to receive MIDI messages, you must provide a callback function to the ```setDelegateFunction``` method. Messages are received as arrays of bytes.

Example :

```
let callback = ( data ) => {
	// do something here...
};
MIDI.setDelegateFunction( callback );
```

### Debug mode

Activate debug output in the console :

```
MIDI.debug(true);
```
