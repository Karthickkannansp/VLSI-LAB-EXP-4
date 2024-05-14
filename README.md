# VLSI-LAB-EXP-4
SIMULATION AND IMPLEMENTATION OF SEQUENTIAL LOGIC CIRCUITS

# AIM: 
 To simulate and synthesis SR, JK, T, D - FLIPFLOP, COUNTER DESIGN using Xilinx ISE.

# APPARATUS REQUIRED:

Xilinx 14.7
Spartan6 FPGA
# PROCEDURE:
STEP:1  Start  the Xilinx navigator, Select and Name the New project.
STEP:2  Select the device family, device, package and speed.       
STEP:3  Select new source in the New Project and select Verilog Module as the Source type.                       
STEP:4  Type the File Name and Click Next and then finish button. Type the code and save it.
STEP:5  Select the Behavioral Simulation in the Source Window and click the check syntax.                       
STEP:6  Click the simulation to simulate the program and  give the inputs and verify the outputs as per the truth table.               
STEP:7  Select the Implementation in the Sources Window and select the required file in the Processes Window.
STEP:8  Select Check Syntax from the Synthesize  XST Process. Double Click in the  FloorplanArea/IO/Logic-Post Synthesis process in the User Constraints process group. UCF(User constraint File) is obtained. 
STEP:9  In the Design Object List Window, enter the pin location for each pin in the Loc column Select save from the File menu.
STEP:10 Double click on the Implement Design and double click on the Generate Programming File to create a bitstream of the design.(.v) file is converted into .bit file here.
STEP:11  On the board, by giving required input, the LEDs starts to glow light, indicating the output.


**LOGIC DIAGRAM**

# SR FLIPFLOP

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/77fb7f38-5649-4778-a987-8468df9ea3c3)

# VERILOG CODE:
```
module srff(s,r,clk,rst,q);
input s,r,clk,rst;
output reg q;
always@(posedge clk)
begin
if(rst==1)
q=0;
else
begin
case({s,r})
2'b00:q=q;
2'b01:q=0;
2'b10:q=1;
2'b11:q=1'bX;
endcase
end
end
endmodule
```
# OUTPUT WAVEFORM:
![image](https://github.com/Karthickkannansp/VLSI-LAB-EXP-4/assets/161430429/ae5b8454-6473-468a-bace-e7d0f996e016)



# JK FLIPFLOP

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/1510e030-4ddc-42b1-88ce-d00f6f0dc7e6)

# VERILOG CODE:
```
module jkff(j,k,clk,rst,q);
input j,k,clk,rst;
output reg q;
always@(posedge clk)
begin
if(rst==1)
q=0;
else
begin
case({j,k})
2'b00:q=q;
2'b01:q=0;
2'b10:q=1;
2'b11:q=~q;
endcase
end
end
endmodule
```
# OUTPUT WAVEFORM:
![image](https://github.com/Karthickkannansp/VLSI-LAB-EXP-4/assets/161430429/79d728df-cafe-4f3a-9864-6044805f44d3)


# T FLIPFLOP

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/7a020379-efb1-4104-85ee-439d660baa08)

# VERILOG CODE:
```
module tff(clk,rst,t,q);
input clk,rst,t;
output reg q;
always @(posedge clk)
begin
if (rst==1)
q=1'b0;
else if (t==0)
q=q;
else
q=~q;
end
endmodule
```
# OUTPUT WAVEFORM:
![image](https://github.com/Karthickkannansp/VLSI-LAB-EXP-4/assets/161430429/3eb61549-b440-4f48-8c4f-1143874b4b55)



# D FLIPFLOP

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/dda843c5-f0a0-4b51-93a2-eaa4b7fa8aa0)

# VERILOG CODE:
```
module dff(d,clk,rst,q);
input d,clk,rst;
output reg q;
always @(posedge clk)
begin
if (rst==1)
q=1'b0;
else
q=d;
end
endmodule
```
# OUTPUT WAVEFORM:
![image](https://github.com/Karthickkannansp/VLSI-LAB-EXP-4/assets/161430429/f6384497-f538-491e-b6ec-f214a4e6061b)



# COUNTER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/a1fc5f68-aafb-49a1-93d2-779529f525fa)

# UP COUNTER:
# LOGIC DIAGRAN:

![image](https://github.com/Karthickkannansp/VLSI-LAB-EXP-4/assets/161430429/350016b4-bbdf-4c39-8667-ed3c48f6a870)

# VERILOG CODE:
```
module upcounter(clk,rst,count);
input clk,rst;
output[3:0]count;
reg[3:0]count;
always@(posedge clk)
begin
if(rst)
count<=4'b0;
else
count<=count+1;
end
endmodule

```
# OUTPUT WAVEFORM:
![image](https://github.com/Karthickkannansp/VLSI-LAB-EXP-4/assets/161430429/b85b6da1-7858-4c67-a234-321a85462abd)

# DOWN COUNTER:

# LOGIC DIAGRAM:
![image](https://github.com/Karthickkannansp/VLSI-LAB-EXP-4/assets/161430429/6d3202b5-2ac9-4f3e-a152-11d332d3517d)

# VERILOG CODE:
```
module downcounter(clk,rst,count);
input clk,rst;
output[3:0]count;
reg[3:0]count;
always@(posedge clk)
begin
if(rst)
count<=4'b0;
else
count <=count-1;
end
endmodule

```
# OUTPUT WAVEFORM:
![image](https://github.com/Karthickkannansp/VLSI-LAB-EXP-4/assets/161430429/ba4e5ee3-3021-440b-b38f-4bb1cbe2076c)





# MOD 10 COUNTER:

# VERILOG CODE:
```
module mod10(clk,rst,out);
input clk,rst;
output reg [3:0]out;
always@(posedge clk)
begin
if (rst==1 | out==4'b1001)
out=4'b0000;
else
out=out+1;
end
endmodule
```
# OUTPUT WAVEFORM:
![image](https://github.com/Karthickkannansp/VLSI-LAB-EXP-4/assets/161430429/081ed0a7-d2b2-4d23-b247-0a9e1f7dd2e8)

# RIPPLE COUNTER:

# LOGIC DIAGRAM:
![image](https://github.com/Karthickkannansp/VLSI-LAB-EXP-4/assets/161430429/ae10ec6c-87d9-4023-a0fd-0e82fa60bef3)


# VERILOG CODE:
```
module tff(q,clk,rst);
input clk,rst;
output q;
wire d;
dff df1(q,d,clk,rst);
not n1(d,q);
endmodule
module dff(q,d,clk,rst);
input d,clk,rst;
output q;
reg q;
always @(posedge clk or posedge rst)
begin
if (rst)
q=1'b0;
else 
q=d;
end
endmodule
module ripplecounter(clk,rst,q);
input clk,rst;
output [3:0]q;
tff tf1(q[0],clk,rst);
tff tf3(q[2],q[1],rst);
tff tf4(q[3],q[2],rst);
endmodule
```
# OUTPUT WAVEFORM:
![image](https://github.com/Karthickkannansp/VLSI-LAB-EXP-4/assets/161430429/aaca140e-2fbd-41e5-858d-7cb7915ab162)





# RESULT
Hence the SR, JK, T, D - FLIPFLOPS, COUNTER DESIGNS are simulated and synthesised using Xilinx ISE.


