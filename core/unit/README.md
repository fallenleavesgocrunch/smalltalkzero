# Units and Quantities

It is smarter to program with units than without. What is a 10 after all when it should be 10 bytes?
We can create an array as either (array of: u8 length: 10) but how do we describe what we would create?
with a quantity: {quantity of: u8 | magnitude: 10}

SI units and their derived units exist as pre-made quantity classes which lets you write:
100 seconds // returns a {quantity of: second | magniature: 100}

You can describe the processing rate of your data with your own classes combined with SI units.
processing-speed-type = person / second
processing-speed-quantity = quantity of: processing-speed-type

When adding or substracting two quantities if their base unit doesn't match there is a compile time error.
This can avoid a lot of numerical type bugs. The unit system has no overhead on runtime, only compile time.

When describing bytes or bits you can define an array type without having to specify a second parameter
for length:
my-buffer = array of: 4 kilobytes


Every base and derived unit used is assigned a unique id that is a prime number allowing any combination
of unit to be combined through multiplication and division. meter^2 is meter id * meter id while byte/second
is byte id / second id. These id's are assigned lazily as they are needed in your code at compile time.
