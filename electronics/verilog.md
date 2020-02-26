
/********************************************************************************************************
Hardware Description Language (VERILOG) -- Essence
********************************************************************************************************/
1.Essence of FPGA
	1.array of logic cells (LUTs + Regs + MuXs)

2.Design flow:
	1.verilog => synthesis => netlist
	2.netlist => PNR (assign gate groups to LUTS) => bitstream for configuration
	3.bitstream download to FPGA

3.Advanced design flow:
	1.Partition the tasks to software and hardware accelerators
	2.Develope hardware, including the hardware accelerators and I/O peripherals,and integrate it with the processor
	3.Develope software
	4.Hardware and software implementation

4.Advantage:
	1.parallel execution
	2.Rapid prototyping and flexibility
	3.deterministic behaviour with multiple time-critical tasks
	4.cost lies in maintainance, low initial cost

/********************************************************************************************************
Hardware Description Language (VERILOG) -- Structural Coding
********************************************************************************************************/
1.The If-else Statement
version1:
	module mux4to1(W,S,f)(
		input [3:0]W,
		input [1:0]S,
		output reg f
	);

		always@(*)
			if(S==0)
				f=W[0];
			else if(S==1)
				f=W[1];
			else if(S==2)
				f=W[2];
			else if(S==3)
				f=W[3];
	endmodule

version2:
	assign f = (S==0) ? W[0] :
				(S==1) ? W[1]:
				(S==2) ? W[2]:
				(S==3) ? W[3]: 1'b0;


2.The Bi-directional Port (can only be used on I/O pins in cycloneII)
	module bi_port(
		inout wire bi;
		....
	);

	assign sig_out = some output expression;

	assign sig_in = bi;
	assign bi = (tri_enable) ? sig_out: 1'z;

	assign some signal = expression with sig_in

	endmodule





/********************************************************************************************************
Hardware Description Language (VERILOG) -- Reference
********************************************************************************************************/
1.Number Representation:
	1.Number Syntax: (sign)(bit width)'(format)(value)
		1.sign: + -
		2.bit width: 8,16,32 or arbitrary
			1.if specified:
				1.if actual size smaller than specified, then zero are padded
				2.in case MSB is x,z or signed, then MSB is padded
			2.not specified:
				1.all unspecified number are 32 bits
		3.format: b(binary),o(octal),h(hex),d(decimal)
		4.value: numeric value corresponds to the format

	2.Binary Conversion (23 => 10111)
		23
		23/2	11	1
		11/2	5	1
		5/2		2	1
		2/2		1	0
		1/2		0	1

	3.Signed Number
		1.1's Complement: reverse all bits [K=(2^n-1)-P]
		2.2's Complement: keep till and include first 1, reverse all bits on the left [K=(2^n)-P]

	4.Other Number:
		1.z (high impedence): can only be synthesized with a tri-state buffer
			1. assign y = (output_enable) ? tri_input : 1'bz;
			2. main application: bidireactional I/O

--------------------------------------------------------------------------------------------------------------
2.Operators
	1.Operands:
		1.Vectors:A[2:0];B[2:0];C[2:0];
		2.Scalars:f;w;

	2.Bitwise Operators
		1.C=~A;		=> 1's complement all bits
		2.C=A&B;	=> AND all bits
		3.C=A~^B	=> XNOR all bits
		4.f=A^B		=> only XOR the least significant bit
		5.P=4'b101x Q=4'b1001	=>P&Q=4'b100x

	3.Logical Operators
		1.C=!A;		=> complement of the sum of all bits
		2.C=A&&B;	=> AND the Sum-of-bits of the two vectors

	4.Reduction Operators
		1.f=&A;		=> AND all bits
		2.f=^A;		=> XOR all bits

	5.Arithmetic Operators
		1.C=A+B;	=> add A and B
		2.C=A-B;	=> subtract B from A
		3.C=-A;		=> 2's complement of A

	7.Equality Operators
		1.(A==B)	=> evaluated as true if equals

	8.Shift Operators
		1.B=A<<1;	=> shifts left for 1 bit
		2.B=A>>2;	=> shifts right for 2 bits

	9.Concatente Operator
		1.D={A,B};	=> combined into a larger vector of 6 bits

	10.Replication Operator
		1.D={3{A}};	=> combined into 3 A
		2.D={4{2'b10}};	=> combined into 10101010

--------------------------------------------------------------------------------------------------------------
2.Half-Adder(HA)
	s=x(+)y;
	c=x&y

--------------------------------------------------------------------------------------------------------------
3.Full-Adder(FA)
	Si=Xi(+)Yi+(+)Ci
	Ci+1=XiYi+XiCi+YiCi

**************************************************************************************
module adder4(carryin,X,Y,S,carryout) //main program
	input carryin;
	input [3:0]X,Y;
	output [3:0]S;
	output carryout;
	wire [3:1]C;

	fulladd stage0 (carryin,X[0],Y[0],S[0],C[1]);
	fulladd stage1 (C[1],X[1],Y[1],S[1],C[2]);
	fulladd stage2 (C[2],X[2],Y[2],S[2],C[3]);
	fulladd stage3 (C[3],X[3],Y[3],S[3],carryout);
endmodule

module fulladd(Cin,x,y,s,Cout)						//the adder component
	input Cin,x,y;
	output s,Cout;

	assign s=x^y^Cin;
	assign Cout=(x&y)|(x&Cin)|(y&Cin);
endmodule
**************************************************************************************


**************************************************************************************
module adder4_with_overflow(carryin,X,Y,S,carryout,overflow)
	parameter n=32
	input carryin;
	input [n-1:0]X,Y;
	output reg[n-1:0]S
	output reg carryout,overflow;

	always@(X or Y or carryin);
	begin
		{carryout,S}=X+Y+carryin;
		overflow=carryout^X[n-1]^Y[n-1]^S[n-1];
	end

endmodule
**************************************************************************************

--------------------------------------------------------------------------------------------------------------
4.Subtractor
	1.principle: 2's Complement is the 1's complement plus 1
	2.modification on Adder:
		1.XOR all subtrahend bits with the SUB(or complement of ADD signal) input signal
		2.Connect C0 with SUB(or complement of ADD signal)
--------------------------------------------------------------------------------------------------------------
5.Overflow
	1.Overflow=Cn-1(+)Cn
--------------------------------------------------------------------------------------------------------------

--------------------------------------------------------------------------------------------------------------
7.Floating-point Representation
	1.Single-precision:+/- 1.M x 2^(E-127)
	2.Double-precision:+/- 1.M x 2^(E-1023)
--------------------------------------------------------------------------------------------------------------
8.Shannon's Expansion Theorem
	f(w1,w2,....wn)= !w1 .f(something)+ w1_f(something)
--------------------------------------------------------------------------------------------------------------
9.The Conditional Operator
	conditional expression ? true_expression : false_expression

module mux2to1(w0,w1,s,f);
	input w0,w1,s;
	output f;

	assign f=s?w1:w0;
endmodule

--------------------------------------------------------------------------------------------------------------


--------------------------------------------------------------------------------------------------------------
11.The Case Statement

module mux4to1(W,S,f)
	input [0:3]W;
	input [1:0]S;
	output reg f;

	always@(W or S)
		case(S)
			0:f=W[0];
			1:f=W[1];
			2:f=W[2];
			3:f=W[3];
		endcase
endmodule
--------------------------------------------------------------------------------------------------------------
12.The For Loop

for(initial_index;terminal_index;increment) statement;

module dec2to4(W,Y,EN)
	input [1:0]W;
	input EN;
	output reg [0:3]Y;
	integer k;

	always@(W or EN)
		for(k=0;k<=3;k=k+1)
			if((w==k))&&(EN=1))
				Y[k]=1;
			else
				Y[k]=0
endmodule
