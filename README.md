## Name: Siranjeevi.S
## Ref no: 23012822

# Exp-6-Synchornous-counters - up counter and down counter 

### AIM: To implement 4 bit up and down counters and validate  functionality.
### HARDWARE REQUIRED:  – PC, Cyclone II , USB flasher
### SOFTWARE REQUIRED:   Quartus prime
### THEORY 

## UP COUNTER 
The counter is a digital sequential circuit and here it is a 4 bit counter, which simply means it can count from 0 to 15 and vice versa based upon the direction of counting (up/down). 

The counter (“count“) value will be evaluated at every positive (rising) edge of the clock (“clk“) cycle.
The Counter will be set to Zero when “reset” input is at logic high.
The counter will be loaded with “data” input when the “load” signal is at logic high. Otherwise, it will count up or down.
The counter will count up when the “up_down” signal is logic high, otherwise count down

Since we know that binary count sequences follow a pattern of octave (factor of 2) frequency division, and that J-K flip-flop multivibrators set up for the “toggle” mode are capable of performing this type of frequency division, we can envision a circuit made up of several J-K flip-flops, cascaded to produce four bits of output.
The main problem facing us is to determine how to connect these flip-flops together so that they toggle at the right times to produce the proper binary sequence.
Examine the following binary count sequence, paying attention to patterns preceding the “toggling” of a bit between 0 and 1:
Binary count sequence, paying attention to patterns preceding the “toggling” of a bit between 0 and 1.

Note that each bit in this four-bit sequence toggles when the bit before it (the bit having a lesser significance, or place-weight), toggles in a particular direction: from 1 to 0.



 
 

Starting with four J-K flip-flops connected in such a way to always be in the “toggle” mode, we need to determine how to connect the clock inputs in such a way so that each succeeding bit toggles when the bit before it transitions from 1 to 0.

The Q outputs of each flip-flop will serve as the respective binary bits of the final, four-bit count:

 
 

Four-bit “Up” Counter
![image](https://user-images.githubusercontent.com/36288975/169644758-b2f4339d-9532-40c5-af40-8f4f8c942e2c.png)



## DOWN COUNTER 

As well as counting “up” from zero and increasing or incrementing to some preset value, it is sometimes necessary to count “down” from a predetermined value to zero allowing us to produce an output that activates when the zero count or some other pre-set value is reached.

This type of counter is normally referred to as a Down Counter, (CTD). In a binary or BCD down counter, the count decreases by one for each external clock pulse from some preset value. Special dual purpose IC’s such as the TTL 74LS193 or CMOS CD4510 are 4-bit binary Up or Down counters which have an additional input pin to select either the up or down count mode.
![image](https://user-images.githubusercontent.com/36288975/169644844-1a14e123-7228-4ed8-81a9-eb937dff4ac8.png)


4-bit Count Down Counter
### Procedure

### 1.Create a New Project:

Open Quartus and create a new project by selecting "File" > "New Project Wizard." Follow the wizard's instructions to set up your project, including specifying the project name, location, and target device (FPGA).

### 2.Create a New Design File:

Once the project is created, right-click on the project name in the Project Navigator and select "Add New File." Choose "Verilog HDL File" or "VHDL File," depending on your chosen hardware description language. ⦁ Write the Combinational Logic Code:Open the newly created Verilog or VHDL file and write the code for your combinational logic. 

### 3.Compile the Project:

To compile the project, click on "Processing" > "Start Compilation" in the menu. Quartus will analyze your code, synthesize it into a netlist, and perform optimizations based on your target FPGA device.

### 4.Analyze and Fix Errors:

If there are any errors or warnings during the compilation process, Quartus will display them in the Messages window. Review and fix any issues in your code if necessary. View the RTL diagram. 

### 5.Verification: 

Click on "File" > "New" > "Verification/Debugging Files" > "University Program VWF". Once Waveform is created Right Click on the Input/Output Panel > " Insert Node or Bus" > Click on Node Finder > Click On "List" > Select All.Give the Input Combinations according to the Truth Table and then simulate the Output Waveform.



## PROGRAM: 

### UPCOUNTER:

~~~
module upCounters(clk, A);
input clk;
output reg [2:0]A;
always @(posedge clk)
begin
   A[2]=(((A[0])&(A[1]))^A[2]);
   A[1]=(A[0])^A[1];
   A[0]=A[0]^1;
end
endmodule
~~~

### DOWNCOUNTER:

~~~
module downCounters(clk,A);
input clk;
output reg [2:0]A;
always @(posedge clk)
begin
   A[2]=(((~A[0])&(~A[1]))^A[2]);
   A[1]=(~A[0])^A[1];
   A[0]=1^A[0];
end 
endmodule
~~~



## RTL REALIZATION:

### UPCOUNTER

![291951201-c283eff0-f438-409e-a830-d3f19628f97e](https://github.com/dineshdharank/Exp-7-Synchornous-counters-/assets/145980096/532ba250-03cc-47e6-8339-ed75b0618255)

### DOWNCOUNTER

![291954208-53eb74d4-fa80-492e-9d7a-813135622b79](https://github.com/dineshdharank/Exp-7-Synchornous-counters-/assets/145980096/b4eb8ad7-7ffd-4f65-a376-665cf17377de)



## TIMING DIGRAMS FOR COUNTER:  

### UPCOUNTER

![291953656-d2839b5b-07e0-4c88-b78e-c36641f63b8a](https://github.com/dineshdharank/Exp-7-Synchornous-counters-/assets/145980096/739f6967-15a8-484b-a815-410f5235a90a)

### DOWNCOUNTER

![291955299-75cbd884-cb5e-4d59-a459-f7f20073e15f](https://github.com/dineshdharank/Exp-7-Synchornous-counters-/assets/145980096/1647ed12-cbe5-4b19-96cc-c5eddd23d885)



## TRUTH TABLE:

### UPCOUNTER

![291951723-c2b57cce-4b4d-426b-aa7a-1241118a14cf](https://github.com/dineshdharank/Exp-7-Synchornous-counters-/assets/145980096/b9f19c8a-f734-4034-abb6-26e9a2965023)

### DOWNCOUNTER

![291954819-e72783bc-a5a2-4f57-b2d2-a06399205dba](https://github.com/dineshdharank/Exp-7-Synchornous-counters-/assets/145980096/06cb501c-8d5b-4320-a68e-11b9c207f17c)


## RESULTS: 

By this we have verified the truth table of 4-bit up-counter using verilog.
