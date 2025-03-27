# [vgen_basic_03](https://github.com/shailja-thakur/VGen/blob/main/prompts-and-testbenches/basic3/prompt2_priority_encoder.v)
## Prompt
please finish this module according to the specification
```verilog
// This is a 3-bit priority encoder. It outputs the position of the first high bit.
module priority_encoder( 
input [2:0] in,
output reg [1:0] pos ); 
// If none of the input bits are high (i.e., input is zero), output zero.
// assign the position of the highest bit of in to pos
```
## Reply
Here is the completed Verilog module priority_encoder that implements a 3-bit priority encoder:
```verilog
// This is a 3-bit priority encoder. It outputs the position of the first high bit.
module priority_encoder( 
    input [2:0] in,
    output reg [1:0] pos 
);
    always @(*) begin
        if (in[2])       // Check the highest bit first
            pos = 2'b10; // Position 2
        else if (in[1])  // Check the second-highest bit
            pos = 2'b01; // Position 1
        else if (in[0])  // Check the lowest bit
            pos = 2'b00; // Position 0
        else
            pos = 2'b00; // Default to 0 if no bits are high
    end
endmodule
```
Explanation:
The always @(*) block ensures that the logic is evaluated whenever the input in changes.
The priority is given to the highest bit (in[2]), followed by in[1], and then in[0].
If none of the bits are high (i.e., in is 3'b000), the output pos defaults to 2'b00.