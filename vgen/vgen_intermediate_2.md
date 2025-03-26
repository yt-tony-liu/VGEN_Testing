# [vgen_intermediate_2](https://github.com/shailja-thakur/VGen/blob/main/prompts-and-testbenches/intermediate2/prompt3_counter.v)
## Prompt
please finish this module according to the specification
```
// This is a counter that counts from 1 to 12
module counter( 
input clk,
input reset,
output reg [3:0] q
); 
// update q on the positive edge of the clock according to the following cases:
// on reset, assign q to 1
// else if q is 12, assign q to 1
// else, increment q by 1 
```
## Reply
Here is the completed Verilog module counter that implements a counter counting from 1 to 12:
```
// This is a counter that counts from 1 to 12
module counter( 
    input clk,
    input reset,
    output reg [3:0] q
); 
    always @(posedge clk or posedge reset) begin
        if (reset) 
            q <= 4'b0001; // On reset, assign q to 1
        else if (q == 4'b1100) 
            q <= 4'b0001; // If q is 12, reset q to 1
        else 
            q <= q + 1; // Otherwise, increment q by 1
    end
endmodule
```
Explanation:
Reset Logic: When reset is high, the counter is set to 1 (4'b0001).
Wrap Around: When q reaches 12 (4'b1100), it wraps back to 1.
Increment: On every positive clock edge, if neither of the above conditions is true, the counter increments by 1.