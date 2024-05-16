# SIMULATION AND IMPLEMENTATION OF FINITE STATE MACHINE
# AIM:
To simulate and synthesis finite state machine using vivado2023.3.
# APPARATUS REQUIRED:
vivado 2023.3
# procedure:
STEP:1 Start the vivado software, Select and Name the New project.
STEP:2 Select the device family, device, package and speed.
STEP:3 Select new source in the New Project and select Verilog Module as the Source type.
STEP:4 Type the File Name and module name and Click Next and then finish button. Type the code and save it.
STEP:5 Select the run simulation and then run Behavioral Simulation in the Source Window and click the check
syntax.
STEP:6 Click the simulation to simulate the program and give the inputs and verify the outputs as per the truth table.
STEP:7 compare the output with truth table.
# Logic Diagram :
![image](https://github.com/navaneethans/VLSI-LAB-EXP-5/assets/6987778/34ec5d63-2b3b-4511-81ef-99f4572d5869)
# VERILOG CODE:
~~~
module Sequence_Detector_Moore(clock,reset,sequence_in,detector_out);
input clock, reset, sequence_in; 
output reg detector_out; 
parameter  S0=2'b00,S1=2'b01,S2=2'b10,S3=2'b11;
reg [1:0] current_state, next_state; 
// sequential memory of the Moore FSM
always @(posedge clock, posedge reset)
begin
 if(reset==1) 
 current_state <= S0;
 else
 current_state <= next_state; 
end 
// to determine next state 
always @(current_state,sequence_in)
begin
 case(current_state) 
 	S0:begin
		if(sequence_in==1)
   			next_state = S1;
  		else
   			next_state = S0;
 	   end
 	S1:begin
if(sequence_in==0)
   			next_state = S2;
  		else
   			next_state = S1;
 	   end
S2:begin
  	if(sequence_in==1)
   		next_state = S3;
 	 else
   		next_state = S0;
    end 
  S3:begin
  	if(sequence_in==0)
   		next_state = S0;
  	else
   		next_state = S1;
     end
	default:next_state = S0;
endcase
end
// to determine the output of the Moore FSM, output only depends on current state
always @(current_state)
begin 
 case(current_state) 
 	S0:   detector_out = 0;
 	S1:   detector_out = 0;
 	S2:  detector_out = 0;
 	S3:  detector_out = 1;
 	default:  detector_out = 0;
 endcase
end 
endmodule
~~~
# OUTPUT:
![fsm11](https://github.com/CalebSamraj14/VLSI-LAB-EXP-5/assets/163808923/89457bfc-2a68-47e9-8a46-f26c4fbcb487)


# RESULT:

Thus the simulate and synthesis finite state machine using vivado2023.3 is verified
