# [vgen_intermediate_6](https://github.com/shailja-thakur/VGen/blob/main/prompts-and-testbenches/intermediate6/prompt3_ram.v)
## Prompt
please finish this module according to the specification
```verilog
// This is a RAM module
module ram #( parameter ADDR_WIDTH=6, parameter DATA_WIDTH=8) 
(input [DATA_WIDTH-1:0] data, input [ADDR_WIDTH-1:0] addr, input we, clk, output [DATA_WIDTH-1:0] q);
reg [DATA_WIDTH-1:0] ram[2**ADDR_WIDTH-1:0];
// when we is high, write data to ram at address addr
// assign the ram value at address addr to q
```
## Reply
Here is the completed Verilog module ram that implements the specified RAM functionality:
```verilog
// This is a RAM module
module ram #( 
    parameter ADDR_WIDTH = 6, 
    parameter DATA_WIDTH = 8
) (
    input [DATA_WIDTH-1:0] data, 
    input [ADDR_WIDTH-1:0] addr, 
    input we, 
    input clk, 
    output reg [DATA_WIDTH-1:0] q
);
    // Declare the RAM as a 2D register array
    reg [DATA_WIDTH-1:0] ram[2**ADDR_WIDTH-1:0];

    always @(posedge clk) begin
        if (we) 
            ram[addr] <= data; // Write data to RAM at the given address when write enable (we) is high
        q <= ram[addr]; // Read the value at the given address and assign it to q
    end
endmodule
```
Explanation:
RAM Declaration:

The RAM is declared as a 2D register array with DATA_WIDTH bits per word and 2**ADDR_WIDTH words.
Write Operation:

When the we (write enable) signal is high, the input data is written to the RAM at the address specified by addr.
Read Operation:

On every clock cycle, the value stored in the RAM at the address addr is assigned to the output q.
Clocked Behavior:

Both read and write operations are synchronized to the positive edge of the clock (clk).
This implementation ensures that the RAM module behaves as specified, supporting both read and write operations.