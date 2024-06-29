# Smart-Aqua

*Digital Electronics  Project  ![](Aspose.Words.d72dd6f4-1ae4-46b8-9077-e42817bb4678.001.png)![](Aspose.Words.d72dd6f4-1ae4-46b8-9077-e42817bb4678.002.png)*

*Satvik Prasad S 2022MT11279* 

**Smart Aqua:** 

**Introduction:** 

Smart Aqua is an innovative solution aimed at addressing the challenge of providing accessible and affordable drinking water in various locations. By leveraging digital logic and Verilog programming, Smart Aqua offers a user-friendly vending system that dispenses water in two predefined quantities: 5 liters and 10 liters. The system is designed to accept denominations of Rs. 5 and Rs. 10 only, ensuring simplicity and convenience for users.

**System Overview:** 

The Smart Aqua vending system operates based on a predefined set of states, each representing a specific stage in the vending process. These states are carefully designed to facilitate seamless interactions between the user, the vending machine, and the water dispensing mechanism. The system architecture ensures efficient utilization of resources while maintaining reliability and robustness.

**Functionality:** 

Quantity Selection: Users can choose between two predefined quantities of water: 5 liters and 10 liters. Each quantity corresponds to a specific price point: Rs. 15 for 5 liters and Rs. 25 for 10 liters. 

Payment Mechanism: The vending machine accepts denominations of Rs. 5 and Rs. 10. Users can insert the required amount of money into the machine to initiate the water dispensing process. 

State Diagram: The vending system is represented by a state diagram, which illustrates the various states and transitions involved in the vending process. For the 5-liter quantity, the system comprises three states, while for the 10-liter quantity, there are five states. Each state defines the conditions for accepting input money, validating the payment, and dispensing water accordingly. 

**For 5 Liters:** 

![](Aspose.Words.d72dd6f4-1ae4-46b8-9077-e42817bb4678.003.jpeg)

**For 10 Liters:** 

![](Aspose.Words.d72dd6f4-1ae4-46b8-9077-e42817bb4678.004.jpeg)

` `Here we have displayed the returned money using BCD and 7 segment display. Which will be easy for the users. 

` `We have given a way to decline the purchase ; that is at every clock edge we evaluate the conditions ; if the user want to decline it He should simply shouldn’t enter any input amount ; and we return the complete amount which may be given by user , that is **0**,**5,10,15,20**  also we display the respective amount in 7-Segment Display** 

**Procedure for purchase:** 

1. Select the quantity . 
1. Start the input of Money. 
1. After respective money , water and change will be returned.


**Conventions:** 

1. Change is 4 bit Binary number ABCD, where if A is 1 it represents change =5 ; B =1 represents  change = 10 , C=1 represent change =15, D=1 represents change=20.
1. Digit1 and Digit0 are driver inputs to BCD of each 7-seg display. 
1. We have given system clock of 5 seconds. 

**STATES TRANSITIONS For 5 Liters:** 

S0: 0 Rs in Smart Aqua –  

- If nothing added: Stay on State 0, OUTPUT = 0, CHANGE = 0. 
- If 5 Rs added: Move to State 1, OUTPUT = 0, CHANGE = 0. 
- If 10 Rs added: Move to State 2, OUTPUT = 0, CHANGE = 0. 

S1: 5 Rs in Smart Aqua –  

- If nothing added: Here, this means the Smart Aqua waited some time but no money was 

added signifying an incomplete transaction, thus the Smart Aqua should return back the money added as CHANGE (5 Rs). No water will be dispensed. Move to State 0, OUTPUT = 0, CHANGE = Rs 5 (01). 

- If 5 Rs added: Move to State 1, OUTPUT = 0, CHANGE = 0. 
- If 10 Rs added: Adding 10 Rs means the Smart Aqua now has 15 Rs total thus, water will be 

dispensed with no CHANGE. Move to State 0, OUTPUT = 1, CHANGE = Rs 0. 

S2: 10 Rs in Smart Aqua –  

- If nothing added: Again, incomplete transaction thus Smart Aqua returns the money added 

as CHANGE (10 Rs). No water will be dispensed. Move to State 0, OUTPUT = 0, CHANGE = Rs 10 (10). 

- If 5 Rs added: Signifies a complete transaction, water will be dispensed. The 5 Liters costs 

15 Rs. 7 with no CHANGE. Move to State 0, OUTPUT = 1, CHANGE = Rs 0. 

- If 10 Rs added: Here the customer overpaid, thus water will be dispensed but with CHANGE 

(5 Rs). Move to State 0, OUTPUT = 1, CHANGE = Rs 5 (01). 

**Truth Table: For 5 Liters :** 



|Qn |in |Qn+1|Change |out1 |
| - | - | - | - | - |
|0 |00' |0 |0000' |0 |
|0 |01' |1 |0000' |0 |
|0 |10' |2 |0000' |0 |
|1 |00' |0 |0001' |0 |
|1 |01' |2 |0000' |0 |
|1 |10' |0 |0000' |1 |
|2 |00' |0 |0010' |0 |
|2 |01' |0 |0000' |1 |
|2 |10' |0 |0001' |1 |

**For 10 Liters:** 



|Qn |in |Qn+1 |Change |out2 |
| - | - | - | - | - |
|0 |00' |0 |0000' |0 |
|0 |01' |1 |0000' |0 |
|0 |10' |2 |0000' |0 |
|1 |00' |0 |0001' |0 |
|1 |01' |2 |0000' |0 |
|1 |10' |3 |0000' |0 |
|2 |00' |0 |0010' |0 |
|2 |01' |3 |0000' |0 |
|2 |10' |4 |0000' |0 |
|3 |00' |0 |0100' |0 |
|3 |01' |4 |0000' |0 |
|3 |10' |0 |0000' |1 |
|4 |00' |0 |1000' |0 |
|4 |01' |0 |0000' |1 |
|4 |10' |0 |0001' |1 |

**Wave Forms:** 

![](Aspose.Words.d72dd6f4-1ae4-46b8-9077-e42817bb4678.005.jpeg)

Here We have selected 5 Liters and the money input  5 , 5 , 10 . So we have out1 =1 and change =5. 

After the reset we have changed all the variables to state0. 

![](Aspose.Words.d72dd6f4-1ae4-46b8-9077-e42817bb4678.006.jpeg)

Here we have selected 5 Liters and the money input 5,5, 0 this mean user have to decline the purchase, so we returned the money Rs10.

After reset we have changed all the variables to State0.

![](Aspose.Words.d72dd6f4-1ae4-46b8-9077-e42817bb4678.007.jpeg)

Here we have selected the 10 Liters and input the money as 10,10,10 ; So we have the out2=1 and change =5. 

![](Aspose.Words.d72dd6f4-1ae4-46b8-9077-e42817bb4678.008.png)

Here we have selected the 10 Liters and input money as 5,10,0 . this mean user have to decline the purchase . So we have out2 =0, and Change= 15.

![](Aspose.Words.d72dd6f4-1ae4-46b8-9077-e42817bb4678.009.jpeg)

![](Aspose.Words.d72dd6f4-1ae4-46b8-9077-e42817bb4678.010.jpeg)

**Project Demonstration:** Change = 0

![](Aspose.Words.d72dd6f4-1ae4-46b8-9077-e42817bb4678.011.jpeg)

![](Aspose.Words.d72dd6f4-1ae4-46b8-9077-e42817bb4678.012.jpeg)

` `Change  = 5 

![](Aspose.Words.d72dd6f4-1ae4-46b8-9077-e42817bb4678.013.jpeg)

Change = 15 

![](Aspose.Words.d72dd6f4-1ae4-46b8-9077-e42817bb4678.014.jpeg)

Change = 10 

We have successfully demonstrated the working of the prototype.

**Code For Smart\_Aqua:** 

module smart\_aqua( 

`    `input clk, 

`    `input reset, 

` `input Liters5, 

` `input Liters10, 

`    `input [1:0] in, 

`    `output reg out1, 

` `output reg out2, 

`    `output reg [3:0] change, 

` `output reg [2:0] Digit0,  output reg [2:0] Digit1  

); 

parameter state0 = 2'b00; parameter state1 = 2'b01; parameter state2 = 2'b10; parameter state3 = 2'b11; parameter state4 = 3'b101; reg [1:0] c\_state, n\_state; 

always @(posedge clk) begin 

if (reset == 1) begin 

`        `c\_state = state0; 

`        `n\_state = state0; 

`        `out1 = 0; 

`  `out2 = 0; 

`        `change = 2'b00; 

`        `Digit0 = 3'b000; 

`  `Digit1 = 3'b000; end else 

`        `c\_state = n\_state; 

if (Liters5) begin 

` `case(c\_state) 

`  `state0: 

if (in == 0) begin 

` `n\_state = state0; 

` `out1 = 0; 

` `change = 4'b0000; 

end else if (in == 2'b01) begin 

` `n\_state = state1; 

` `out1 = 0; 

` `change = 4'b0000; 

end else if (in == 2'b10) begin 

` `n\_state = state2; 

` `out1 = 0; 

` `change = 4'b0000; 

end   state1: 

if (in == 0) begin 

` `n\_state = state0; 

` `out1 = 0; 

` `change = 4'b0001; 

end else if (in == 2'b01) begin 

` `n\_state = state2; 

` `out1 = 0; 

` `change = 4'b0000; 

end else if (in == 2'b10) begin 

` `n\_state = state0; 

` `out1 = 1; 

` `change = 4'b0000; 

end 

`  `state2: 

if (in == 0) begin 

` `n\_state = state0; 

` `out1 = 0; 

` `change = 4'b0010; 

end else if (in == 2'b01) begin 

` `n\_state = state0; 

` `out1 = 1; 

` `change = 4'b0000; 

end else if (in == 2'b10) begin 

` `n\_state = state0; 

` `out1 = 1; 

` `change = 4'b0001; 

end  endcase 

end 

if (Liters10) begin 

` `case(c\_state) 

`  `state0: 

if (in == 0) begin 

` `n\_state = state0; 

` `out2 = 0; 

` `change = 4'b0000; 

end else if (in == 2'b01) begin 

` `n\_state = state1; 

` `out2 = 0; 

` `change = 4'b0000; 

end else if (in == 2'b10) begin 

` `n\_state = state2; 

` `out2 = 0; 

` `change = 4'b0000; 

end   state1: 

if (in == 0) begin 

` `n\_state = state0; 

` `out2 = 0; 

` `change = 4'b0001; 

end else if (in == 2'b01) begin 

` `n\_state = state2; 

` `out2 = 0; 

` `change = 4'b0000; 

end else if (in == 2'b10) begin 

` `n\_state = state3; 

` `out2 = 0; 

` `change = 4'b0000; 

end 

`  `state2: 

if (in == 0) begin 

` `n\_state = state0;  out2 = 0; 

` `change = 4'b0010; 

end else if (in == 2'b01) begin 

` `n\_state = state3; 

` `out2 = 0; 

` `change = 4'b0000; 

end else if (in == 2'b10) begin 

` `n\_state = state4; 

` `out2 = 0; 

` `change = 4'b0000; 

end 

`  `state3: 

if (in == 0) begin 

` `n\_state = state0; 

` `out2 = 0; 

` `change = 4'b0100; 

end else if (in == 2'b01) begin 

` `n\_state = state4; 

` `out2 = 0; 

` `change = 4'b0000; 

end else if (in == 2'b10) begin 

` `n\_state = state0; 

` `out2 = 1; 

` `change = 4'b0000; 

end   state4: 

if (in == 0) begin 

` `n\_state = state0; 

` `out2 = 0; 

` `change = 4'b1000; 

end else if (in == 2'b01) begin 

` `n\_state = state0; 

` `out2 = 1; 

` `change = 4'b0000; 

end else if (in == 2'b10) begin 

` `n\_state = state0; 

` `out2 = 1; 

` `change = 4'b0001; end 

` `endcase end 

if (change[0]) begin 

` `Digit0 = 3'b101; 

` `Digit1 = 3'b000; end 

if (change[1]) begin 

` `Digit0 = 3'b000; 

` `Digit1 = 3'b001; end 

if (change[2]) begin 

` `Digit0 = 3'b101; 

` `Digit1 = 3'b001; end 

if (change[3]) begin 

` `Digit0 = 3'b000; 

` `Digit1 = 3'b010; end 

end endmodule 

**Test Bench Code:** 

`timescale 1ns/1ns

module smart\_aqua\_tb; 

reg clk, reset, Liters5, Liters10; 

reg [1:0] in; 

wire out1, out2; 

wire [3:0] change; 

wire [2:0] Digit0, Digit1; 

smart\_aqua dut (.clk(clk), .reset(reset), .Liters5(Liters5), .Liters10(Liters10),

.in(in), .out1(out1), .out2(out2), .change(change), .Digit0(Digit0), .Digit1(Digit1)); 

always #5 clk = ~clk; 

initial begin 

`    `$dumpfile("dump.vcd"); $dumpvars(0, smart\_aqua\_tb);

`    `clk = 0; reset = 1; Liters5 = 0; Liters10 = 1; #10 reset = 0; in = 2'b00; #10 in = 2'b10; 

`    `#10 in = 2'b10; #10 in = 2'b10; #10 reset = 1; #10 in = 2'b00; #10 reset = 0; 

`    `#10 $display("Test case 1: No liters inserted - out1=%b, out2=%b, change=%b, Digit0=%b, Digit1=%b",                   out1, out2, change, Digit0, Digit1); 

`    `#10 $finish; 

end 

endmodule 

**Conclusion:** 

Smart Aqua represents a significant advancement in providing accessible drinking water solutions. By leveraging digital logic and Verilog programming, the vending system offers a reliable, user-friendly interface for dispensing water in predefined quantities. With its efficient state-based architecture and intuitive operation, Smart Aqua aims to address the growing need for automated drinking water systems in various settings.
