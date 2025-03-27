# [vgen_basic_01](https://github.com/shailja-thakur/VGen/blob/main/prompts-and-testbenches/basic1/prompt1_wire_assign.v)
## Prompt
please finish this module according to the specification
```verilog
// This is a module that assigns the output to the input
module wire_assign( input in, output out );
```
## Reply
Here is the completed Verilog module wire_assign that assigns the output to the input:
```verilog
// This is a module that assigns the output to the input
module wire_assign( input in, output out );
    assign out = in; // Assign the value of 'in' directly to 'out'
endmodule
```
This module uses a continuous assignment statement (assign) to connect the input in directly to the output out.