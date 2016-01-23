# x10

A library to encapsulate the logic of the [X10 Protocol][2]. Notably, converting addresses, house codes, unit codes and function codes from hexadecimal to standard JavaScript types including Number, String, and JSON.

Used to pipe X10 events between different modules, like from the W800 to the CM11A.

## Install

	npm install x10

## Usage

	var X10Address = require("x10").Address,
		X10Command = require("x10").Command;
	
	var address;
	address = new X10Address("A1");
	address.toNumber(); // 0x66 || 102
	address.toArray(); // [0x6, 0x6]
	
	address = new X10Address(0x66);
	address.toArray(); // [0x6, 0x6]
	address.toString(); // "A1"
	
	address = new X10Address([0x6, 0x6]);
	address.toNumber(); // 0x66 || 102
	address.toString(); // "A1"
	
	var command;
	command = new X10Command("allLightsOff");
	command.toObject(); // {"functionCode": 6}
	
	command = new X10Command(6);
	command.toString(); // "allLightsOff"
	
## Change Log

*1.1.0 — January 23, 2016*

* added test case and support for creating X10Commands from case-insensitive strings

*1.0.1 — January 21, 2016*

* Added toString method for X10Commands

*1.0.0 — January 20, 2016*

* initial version

## License

x10 is available under the [MIT License][1].

  [1]: https://github.com/keithws/x10/blob/master/LICENSE
  [2]: http://en.wikipedia.org/wiki/X10_(industry_standard)
