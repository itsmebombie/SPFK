# BASICS
SPFK is an esoteric language written in SPWN heavily inspired by Brainfuck.
Its purpose is to make adding objects to Geometry Dash a lot harder while still trying to keep Brainfuck's original feel and behaviour.
It currently doesn't write to levels, it only displays the code generated in the console.

For more information regarding how Brainfuck works, please visit [this link](https://docs.google.com/document/d/1M51AYmDR1Q9UBsoTrGysvuzar2_Hx69Hz14tsQXWV6M/edit).

# CUSTOM COMMANDS
SPFK has a syntax that is very similar to Brainfuck's syntax. In fact, all of the commands that exist in Brainfuck behave exactly the same here.
I will only be explaining the new commands that do not exist in Brainfuck.

## \#
This command dumps the current memory and returns it with the rest of the output.
It can dump either 128 cells or the whole memory depending on the chosen settings. (Keep in mind that dumping the whole memory could take a longer time based on the maximum memory cells and your machine)

## ,
This command outputs the current cell's raw value instead of printing the corresponding ascii character.

## @
This command gets the next cells' values and the amount of values it gets depends on the current cell's value * 2 and converts them to a gd object. 
For example, if your memory looks like this `3, 1, 17, 2, 30, 3, 15, 8` and the pointer is pointing at the first cell, it will get the next 6 cells' values (1, 17, 2, 30, 3, 15) and convert them to object "values", in this case, `1` is the object id of our object, `2` is the x position of our object and `3` is the y position of our object, that means that our object has the id of `17`, it is positioned `30` units from the start on the x axis and `15` units from the start on the y axis. For more information on how the object ids work, visit [the SPWN Documentation](http://spu7nix.net/spwn/#).
P.S. Values automatically get converted to a group/color channel/item channel/block channel if needed. For strings/arrays you have to use `$`.

## $
This command gets the next cells' values and the amount of values it gets depends on the current cell's value.
It is only used when a string/array is necessary while adding an object.
For example, if your memory looks like this `3, 67, 70, 73, 94` and the pointer is pointing at the first cell, it will either return `[67, 70, 73]` or `CFI` depending on the situation. 

# USAGE
First of all, copy the folder [spfk](./spfk) in your libraries folder for it to work.

There is only one macro that can be called from the library, and that is `interpreter(code, add_to_level = true, dump_whole_memory = false, max_memory_cells = 30000, max_execution_time = 60)` with 5 parameters. 
The `code` parameter is a mandatory parameter that determines the code the interpreter should execute. 
The `add_to_level` parameter is an optional parameter that determines whether the interpreter will write the objects to the level or output them in the console. This is defaulted to `true`. 
The `dump_whole_memory` parameter is an optional parameter that determines whether the interpreter should dump the whole memory or only a portion of it. This is defaulted to `false`.
The `max_memory_cells` parameter is an optional parameter that determines how large the memory should be. This is defaulted to `30000` cells.
The `max_execution_time` parameter is an optional parameter that determines how many seconds the script should be executing for before the interpreter timing out. This is defaulted to `60` seconds.

An example on how to use the interpreter macro in an actual script is [here](./spfk/lib.spwn).

# OTHERS
To compile the level, you have to end any loops running in the background, in the example given, you can do that by  typing `exit` or `compile`.
Keep in mind that the interpreter will always dump the memory after executing the script, and it will return it along with the output (`return {output: output, dump: dump}`).

If something is unclear, please tell me so I can make it easier to understand!
