# [vgen_basic_04](https://github.com/shailja-thakur/VGen/blob/main/prompts-and-testbenches/basic4/prompt3_mux.v)
## Prompt
please finish this module according to the specification
```verilog
// This is a 2-to-1 multiplexer.
module mux(
input [4:0] a, b,
input sel,
output [4:0] out );
// When sel=0, assign a to out. 
// When sel=1, assign b to out.
```
## Reply
Here is the completed Verilog module mux that implements a 2-to-1 multiplexer:
```verilog
// This is a 2-to-1 multiplexer.
module mux( 
    input [4:0] a, b,
    input sel,
    output [4:0] out
);
    assign out = sel ? b : a; // If sel=1, assign b to out; if sel=0, assign a to out
endmodule
```
Explanation:
The assign statement uses a ternary operator (? :) to select between a and b based on the value of sel.
If sel is 0, a is assigned to out.
If sel is 1, b is assigned to out.