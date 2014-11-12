[allgood](https://www.npmjs.org/package/allgood)
======

Super lightweight JSON model validation for node.js

## Installation

	npm install allgood

## Usage

### Validate module

A validation consists of a JSON object to test and a JSON schema, a definition of the model.

The keys in the schema are the keys you expect to find in the test object, and the values of the schema are the expected types of the test object's corresponding values.

	var allgood = require('allgood')
	  valid = allgood.valid;

	var personSchema = {"name":"string", "age":"number"};
	var newPerson = {name:"Harry Potter", "age":11};
	if (valid(personSchema, newPerson)) {
		console.log("You're a wizard, Harry");
	}

### Find errors in module

Helpful feedback string about the problems with an invalid model.
	
	problems = allgood.problems;

	var newPerson = {name:"Ron Weasley"};
	if (valid(personSchema, newPerson)) {
		console.log("You're a wizard, Ron");
	} else {
		error = problems(personSchema, newPerson); // contains 'message', 'missingKeys', 'incorrectKeyValues'
		console.log(error.message);
		console.log('Missing ' + error.missingKeys);
		console.log('Wrong type for ' + error.incorrectKeyValues);
	}
	

## Tests

	npm test
