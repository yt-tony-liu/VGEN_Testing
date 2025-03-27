# [vgen_advanced_1](https://github.com/shailja-thakur/VGen/blob/main/prompts-and-testbenches/advanced1/prompt2_signed-addition-overflow.v)
## Prompt
please finish this module according to the specification
```verilog
// This is a signed adder that adds two 8-bit 2's complement numbers. It also captures a signed overflow.
module signed_adder(input [7:0] a, input [7:0] b, output [7:0] s, output overflow ); 
// The numbers a and b are added to the output s. 
// The signed overflow of a and b is assigned to the output overflow.
```
## Reply
Here is the completed Verilog module signed_adder that implements the signed addition and detects overflow:
```verilog
// This is a signed adder that adds two 8-bit 2's complement numbers. It also captures a signed overflow.
module signed_adder(
    input [7:0] a, 
    input [7:0] b, 
    output [7:0] s, 
    output overflow
);
    assign s = a + b; // Perform the addition

    // Detect signed overflow
    assign overflow = (~a[7] & ~b[7] & s[7]) | (a[7] & b[7] & ~s[7]);
endmodule
```
Explanation:
Addition:

The two 8-bit 2's complement numbers a and b are added, and the result is assigned to the output s.
Signed Overflow Detection:

Overflow occurs in signed addition when:
Both a and b are positive (a[7] == 0 and b[7] == 0), but the result s is negative (s[7] == 1).
Both a and b are negative (a[7] == 1 and b[7] == 1), but the result s is positive (s[7] == 0).
```verilog
(~a[7] & ~b[7] & s[7]) | (a[7] & b[7] & ~s[7])
```
This implementation ensures that the signed addition is performed correctly and that signed overflow is accurately detected.