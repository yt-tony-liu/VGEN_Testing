# [vgen_advanced_3](https://github.com/shailja-thakur/VGen/blob/main/prompts-and-testbenches/advanced3/prompt2_advfsm.v)
## Prompt
please finish this module according to the specification
```verilog
// This is a finite state machine that recognizes the sequence 101 on the input signal x. 
module adv_fsm(
input clk,
input reset,
input x,
output z ); 
reg [1:0] present_state, next_state;
parameter IDLE=0, S1=1, S10=2, S101=3;
// output signal z is asserted to 1 when present_state is S101 
// present_state is reset to IDLE when rset is high
// otherwise it is assigned next state
// if present_state is IDLE, next_state is assigned S1 if x is 1, otherwise next_state stays at IDLE
// if present_state is S1, next_state is assigned S10 if x is 0, otherwise next_state stays at IDLE 
// if present_state is S10, next_state is assigned S101 if x is 1, otherwise next_state stays at IDLE 
// if present_state is S101, next_state is assigned IDLE
```
## Reply
Here is the completed Verilog module adv_fsm that implements the specified finite state machine:
```verilog
// This is a finite state machine that recognizes the sequence 101 on the input signal x. 
module adv_fsm(
    input clk,
    input reset,
    input x,
    output reg z
); 
    reg [1:0] present_state, next_state;
    parameter IDLE = 2'b00, S1 = 2'b01, S10 = 2'b10, S101 = 2'b11;

    // State transition logic
    always @(posedge clk or posedge reset) begin
        if (reset)
            present_state <= IDLE; // Reset to IDLE state
        else
            present_state <= next_state; // Update to the next state
    end

    // Next state logic
    always @(*) begin
        case (present_state)
            IDLE: 
                if (x)
                    next_state = S1; // Transition to S1 if x is 1
                else
                    next_state = IDLE; // Stay in IDLE if x is 0
            S1: 
                if (~x)
                    next_state = S10; // Transition to S10 if x is 0
                else
                    next_state = IDLE; // Return to IDLE if x is 1
            S10: 
                if (x)
                    next_state = S101; // Transition to S101 if x is 1
                else
                    next_state = IDLE; // Return to IDLE if x is 0
            S101: 
                next_state = IDLE; // Always return to IDLE from S101
            default: 
                next_state = IDLE; // Default to IDLE
        endcase
    end

    // Output logic
    always @(*) begin
        z = (present_state == S101); // Assert z when in S101
    end
endmodule
```
Explanation:
State Transition Logic:

The present_state is updated on the positive edge of the clock or reset.
If reset is high, the FSM resets to the IDLE state.
Next State Logic:

The next_state is determined based on the present_state and the input x:
From IDLE, transition to S1 if x is 1.
From S1, transition to S10 if x is 0.
From S10, transition to S101 if x is 1.
From S101, always transition back to IDLE.
Output Logic:

The output z is asserted (1) only when the present_state is S101.
This implementation ensures the FSM correctly recognizes the sequence 101 on the input signal x and behaves as specified.