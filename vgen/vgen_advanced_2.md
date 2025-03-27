# [vgen_advanced_2](https://github.com/shailja-thakur/VGen/blob/main/prompts-and-testbenches/advanced2/prompt3_countslow.v)
## Prompt
please finish this module according to the specification
```verilog
// This is a decade counter that counts from 0 through 9, inclusive. It counts only when slowena is high.
module count_slow(input clk, input slowena, input reset, output reg [3:0] q);
// On the positive edge of the clock:
// if reset is high, reset the output q to 0. 
// Otherwise, only increment the output q if the slowena input is high and q is not 9.
```
## Reply
Here is the completed Verilog module count_slow that implements the specified decade counter:
```verilog
// This is a decade counter that counts from 0 through 9, inclusive. It counts only when slowena is high.
module count_slow(
    input clk, 
    input slowena, 
    input reset, 
    output reg [3:0] q
);
    always @(posedge clk or posedge reset) begin
        if (reset)
            q <= 4'b0000; // Reset q to 0 when reset is high
        else if (slowena && q < 4'b1001) 
            q <= q + 1; // Increment q if slowena is high and q is less than 9
    end
endmodule
```
Explanation:
Reset Logic:

When reset is high, the counter q is reset to 0.
Counting Logic:

The counter increments only when:
slowena is high.
The current value of q is less than 9 (4'b1001).
If q reaches 9, it stops incrementing until reset.
Clock Synchronization:

The counter updates on the positive edge of the clock (clk).
This implementation ensures the counter behaves as specified, counting from 0 to 9 inclusively and only incrementing when slowena is high.