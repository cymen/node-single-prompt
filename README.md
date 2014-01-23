# single-prompt [![Build Status](https://travis-ci.org/cymen/single-prompt.png?branch=master)](https://travis-ci.org/cymen/single-prompt)

[![NPM](https://nodei.co/npm/single-prompt.png?downloads=true&stars=true)](https://npmjs.org/package/single-prompt)

`single-prompt` is a simple prompter to get a single character or digit input
from the user on the console. It repeats the prompt until a valid input is
made.

## Example of prompting for a character

    $ cat character.js
    var prompter = require('single-prompt');

    prompter
      .prompt('Are you crazy', ['y', 'n'])
      .then(function(choice) {
          console.log('choice', choice);
      });

    $ node character.js
    Are you crazy [y, n]: a is not a valid choice, please try again
    Are you crazy [y, n]: n
    choice n

## Example of prompting for a number

    $ cat number.js
    var prompter = require('./src/single-prompt');

    prompter
      .prompt('Number of diners', [1, 2, 3, 4, 5])
      .then(function(choice) {
          console.log('choice', choice);
      });

    $ node number.js
    Number of diners [1, 2, 3, 4, 5]: 2
    choice 2

Note that internally `single-prompt` attempts to coerce the key to
the type of the provided choices. If the match is an integer, it will
return an integer so in this example, 2 is of type 'number'. It is
assumed you won't do something silly like prompt with options like
`[1, '1']`. It will work just maybe not quite how you want it to.