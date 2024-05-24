<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
   waveform
</head>
<body>
    <h1>This is a problem statement where the output waveform is already given, and accordingly we have to write the design code.</h1>
    <img src="https://github.com/armaan-says/DIGITAL-SYSTEM-DESIGN/blob/main/Images/simulation.jpg" width=1000 height=600>
<p> This is the design and testbench code for the give output waveform. <br>The output waveform is analysed and then the logic can be determined. <br>From the output waveform, we can observe c ranges from 0 to f(15) in simulation 1 and c ranges from 0 to 8 in simulation 2 </p>
<p> as c=0 output(q) is assigned with the value of b<br>as c=1 output(q) is assigned with the value of e<br>
as c=2 output(q) is assigned with the value of a<br>as c=3 output(q) is assigned with the value of d<br>And for any other value of c(from 4 to f) output(q) is f(15)</p>
<p> Hence using a 4X1 MUX logic we can solve this problem statement </p>


<p>This design code is according to simulation 2 <br> Design Code: </p>    
module mux_d(q,a,b,c,d,e);<br>
input [3:0]a,b,c,d,e;<br>
output reg [3:0]q;<br>
always @(*)<br>
begin<br>
    case({c})<br>
      4'b0000:q=b;<br>
      4'b0001:q=e;<br>
      4'b0010:q=a;<br>
      4'b0011:q=d;<br>
      default:q=4'b1111;<br>
    endcase<br>
end<br>
endmodule<br>
<br>
<p> Testbench code for the above design code <br> This testbench code is according to simulation 2</p>
`timescale 1ns/1ps <br>
module mux_t; <br>
wire [3:0]q; <br>
reg [3:0]a,b,c,d,e; <br>
mux_d uut(q,a,b,c,d,e); <br>
initial <br>
begin <br>
a=4'd1;b=4'd2;d=4'd3;e=4'd4; 
c=4'd0; 
#5 c=4'd1; <br>
#5 c=4'd2; <br>
#5 c=4'd3; <br>
#5 c=4'd4; <br>
#5 c=4'd5; <br>
#5 c=4'd6; <br>
#5 c=4'd7; <br>
#5 c=4'd8; <br>
#5 a=4'd5;b=4'd6;d=4'd7;e=4'd8;
c=4'd0; <br>
#5 c=4'd1; <br>
#5 c=4'd2; <br>
#5 c=4'd3; <br>
#5 c=4'd4; <br>
#5 c=4'd6; <br>
#5 c=4'd6; <br>
#5 c=4'd7; <br>
#5 c=4'd8; <br>
#5 $finish; <br>
end <br>
endmodule <br>
</body>
</html>

 
