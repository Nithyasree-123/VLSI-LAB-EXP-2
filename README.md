# SIMULATION AND IMPLEMENTATION OF  COMBINATIONAL LOGIC CIRCUITS

## AIM: 
To simulate and synthesis ENCODER, DECODER, MULTIPLEXER, DEMULTIPLEXER, MAGNITUDE COMPARATOR using vivado.
## APPARATUS REQUIRED:
vivado 2023.2.
## PROCEDURE:
```
STEP:1 Start the vivado software, Select and Name the New project.

STEP:2 Select the device family, device, package and speed.

STEP:3 Select new source in the New Project and select Verilog Module as the Source type.

STEP:4 Type the File Name and module name and Click Next and then finish button. Type the code and save it.

STEP:5 Select the run simulation and then run Behavioral Simulation in the Source Window and click the check syntax.

STEP:6 Click the simulation to simulate the program and give the inputs and verify the outputs as per the truth table.

STEP:7 compare the output with truth table.
```

**LOGIC DIAGRAM**

### ENCODER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/3cd1f95e-7531-4cad-9154-fdd397ac439e)


### DECODER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/45a5e6cf-bbe0-4fd5-ac84-e5ad4477483b)


### MULTIPLEXER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/427f75b2-8e67-44b9-ac45-a66651787436)


### DEMULTIPLEXER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/1c45a7fc-08ac-4f76-87f2-c084e7150557)


### MAGNITUDE COMPARATOR

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/b2fe7a05-6bf7-4dcb-8f5d-28abbf7ea8c2)

## VERILOG CODE:

### 8-3 ENCODER:
```
module encoder(d,a,b,c);

input [7:0]d; output a,b,c;

or (a,d[4],d[5],d[6],d[7]);

or (b,d[2],d[3],d[6],d[7]);

or (c,d[1],d[3],d[5],d[7]);

endmodule
```
### 3-8 DECODER:
```
module decoder(A,E,Y);

input [1:0]A;

input E;

output [3:0]Y;

assign Y[0]=~A[1]&~A[0]&E;

assign Y[1]=~A[1]&A[0]&E;

assign Y[2]=A[1]&~A[0]&E;

assign Y[3]=A[1]&A[0]&E;

endmodule

module decoder(A,Y);

input[2:0]A;

output[7:0]Y;

decoder_2_4 d1(A[1:0],~A[2],Y[3:0]);

decoder_2_4 d2(A[1:0],~A[2],Y[7:4]);

endmodule
```
### 8-1 MULTIPLEXER:
```
module multi(i,s,y);

input[7:0]i;

input[2:0]s;

output reg y;

always@(*)

begin

case({s[2],s[1],s[0]})

3'b000:y=i[0];

3'b001:y=i[1];

3'b010:y=i[2];

3'b011:y=i[3];

3'b100:y=i[4];

3'b101:y=i[5];

3'b110:y=i[6];

3'b111:y=i[7];

endcase

end

endmodule
```
### 1-8 DEMULTIPLEXER:
 
```
module demultiplexer(d1,d2,d3,d4,d5,d6,d7,d8,i,s0,s1,s2);

input i,s0,s1,s2;

output d1,d2,d3,d4,d5,d6,d7,d8;

wire w1,w2,w3;

not g1(w1,s0);

not g2(w2,s1);

not g3(w3,s2);

and g4(d1,w1,w2,w3,i);

and g5(d2,w1,w2,s2,i);

and g6(d3,w1,s1,w3,i);

and g7(d4,w1,s1,s2,i);

and g8(d5,s0,w2,w3,i);

and g9(d6,s0,w2,s2,i);

and g10(d7,s0,s1,w3,i);

and g11(d8,s0,s1,s2,i);

endmodule

```
### 2 BIT MAGNITUDE COMPARATOR :
```
module mag_com(a,b,gt,it,eq);

input [3:0]a,b;

output reg gt,it,eq;

always @(a,b)

begin

if(a>b)

begin

gt = 1'b1;

it = 1'b0;

eq = 1'b0;

end

else if(a<b)

begin

gt = 1'b0;

it = 1'b1;

eq = 1'b0;

end

else

begin

gt = 1'b0;

it = 1'b0;

eq = 1'b1;

end

end

endmodule
```
## OUTPUT WAVEFORM:
### ENCODER:
<img width="838" alt="316725183-304cc633-f99b-4e88-8a8d-e77ef91b9af9" src="https://github.com/Nithyasree-123/VLSI-LAB-EXP-2/assets/164908713/cc60c07b-682e-4cac-9fa3-03c15a00af63">

### DECODER:
<img width="690" alt="316725214-02c33818-f775-401b-9636-e726b05026c9" src="https://github.com/Nithyasree-123/VLSI-LAB-EXP-2/assets/164908713/d18965b1-bbc8-43de-ab47-9a56fc28d078">

### MULTIPLEXER:
<img width="773" alt="316725241-5d8655d7-1d55-431c-897c-cbe9763890c6" src="https://github.com/Nithyasree-123/VLSI-LAB-EXP-2/assets/164908713/0f4e0f40-f519-447c-aab3-b512f260a2e1">

### DEMULTIPLIXER:
<img width="724" alt="316725790-d97851fe-bc5b-4c44-9057-ebbb28f708c6" src="https://github.com/Nithyasree-123/VLSI-LAB-EXP-2/assets/164908713/a535752f-6150-4f37-9ed9-a583823c1604">

### 2 BIT MANGITUDE COMPARATOR:
<img width="786" alt="316725898-62a21386-fbd6-43ba-b9bd-0ec03cadf3ea" src="https://github.com/Nithyasree-123/VLSI-LAB-EXP-2/assets/164908713/41df3121-3c7b-42dc-a98e-d561d7b8c63e">

## RESULT:
Thus the simulation and synthesis of ENCODER, DECODER, MULTIPLEXER, DEMULTIPLEXER, 2bit MAGNITUDE COMPARATOR using vivado is successfully completed and executed.
