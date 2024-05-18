# VLSI-LAB-EXP-4
SIMULATION AND IMPLEMENTATION OF SEQUENTIAL LOGIC CIRCUITS

# AIM: 
 To simulate and synthesis SR, JK, T, D - FLIPFLOP, COUNTER DESIGN using Xilinx ISE.

# APPARATUS REQUIRED:

Xilinx 14.7
Spartan6 FPGA

# LOGIC DIAGRAM

# SR FLIPFLOP

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/77fb7f38-5649-4778-a987-8468df9ea3c3)


# JK FLIPFLOP

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/1510e030-4ddc-42b1-88ce-d00f6f0dc7e6)

# T FLIPFLOP

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/7a020379-efb1-4104-85ee-439d660baa08)


# D FLIPFLOP

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/dda843c5-f0a0-4b51-93a2-eaa4b7fa8aa0)


# COUNTER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/a1fc5f68-aafb-49a1-93d2-779529f525fa)
# VERILOG CODE
# SR FLIPFLOP:
```
module srff(clk,j,k,rst,q );

input s,r,clk,rst;

output reg q;

always@(posedge clk)

begin

if(rst==1)

q=1'b0;

else

begin

case({s,r})

2'b00: q=q;

2'b01:q=1'b0;

2'b10:q=1'b1;

2'b11:q=1'bx;

endcase

end

end

endmodule
```

# JK FLIPFLOP:
```
module jkff(clk,j,k,rst,q );

input j,k,clk,rst;

output reg q;

always@(posedge clk)

begin

if(rst==1)

q=1'b0;

else

begin

case({j,k})

2'b00: q=q;

2'b01:q=1'b0;

2'b10:q=1'b1;

2'b11:q=~q;

endcase

end

end

endmodule
```
# T FLIPFLOP:
```
module tff(clk,reset,t,q);

input clk,reset,t;

output reg q;

always @(posedge clk)

begin

if(reset==1)

q=0;

else

begin

if(t==0)

q=q;

else

q=~q;

end

end

endmodule
```
# D FLIPFLOP:
```
module dff(clk,d,rst,q );

input d,clk,rst;

output reg q;

always@(posedge clk)

begin

if(rst==1)

q=1'b0;

else

q=d;

end

endmodule
```

#UPDOWN COUNTER:
```
module updown(clk,rst,up_down,count);

input clk,rst,up_down;

output reg[3:0]count;

always@(posedge clk)

begin

if(rst==1)

count <= 4'b0000;

else if (up_down == 1'b1)

count <= count + 1'b1;

else

count <= count-1'b1;

end

endmodule
```
# MOD 10 COUNTER:
```
module mod(clk,rst,count);

input clk,rst;

output reg[3:0]count;

always @(posedge clk)

begin

if(rst==1 | count==4'b1001)

count <= 4'b0000;

else

count <= count +1;

end

endmodule
```
# RIPPLE COUNTER:
```
module ripplecounter(clk,rst,q);

input clk,rst;

output [3:0]q;

tff tff1(q[0],clk,rst);

tff tff2(q[1],q[0],rst);

tff tff3(q[2],q[1],rst);

tff tff4(q[3],q[2],rst);

endmodule

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

always@(posedge clk or posedge rst)

begin

if(rst)

q=1'b10;

else

q=d;

end

endmodule
```
OUTPUT WAVEFORM
# SR flipflop:
![324227165-5a83f8ff-2d6b-49eb-8d7c-eb20c03f7b33](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/160302888/25d75031-11ef-4633-b0b5-8548d0af0a50)
# jk flip flop
![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/160302888/97c7bd62-23e4-4405-94a9-e5059cb1d90b)
# t flip flop
![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/160302888/f0e82e51-92db-42b9-9842-04dcf8454f1e)
# D flip flop
![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/160302888/633a5001-4f63-412f-9bc5-8b1259d7dec9)
# updown counter
![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/160302888/5433e7b0-c4f2-4dcc-aad2-96c19e077ac5)
# mod 10 counter
![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/160302888/09dc66d0-b976-4857-b8af-b8d0e06debfb)

 # resut
thus,the simulation and synthesis of SR,JK,T,D flipflops,counters by using vivado has been successfully excecuted and verified.
