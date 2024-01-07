`timescale 1ns / 1ps
//////////////////////////////////////////////////////////////////////////////////
// Engineer: Ivan Castro
// 
// Create Date: 01/06/2024 11:22:37 AM
// Design Name: NRZ line code to Manchester line code 
// Module Name: NRZ_2_Manchester_Moore
// Target Devices: XC7A100T-1CSG324C
// Tool Versions: 2023.2.1
// Description: This Verilog code will convert NRZ to Manchester using a Moore
//   state machine.  
//////////////////////////////////////////////////////////////////////////////////


module NRZ_2_Manchester_Moore(
    
    input B_in, clock, rst_b,
    
    output reg B_out
    );
    
reg [1:0] state, next_state;

parameter s0 = 2'b00,
          s1 = 2'b01,
          s2 = 2'b10,
          s3 = 2'b11;
          
always @(negedge clock, negedge rst_b)
begin
    if(!rst_b)
        state <= s0;
    else
        state <= next_state;
end

always @ (state or B_in)
begin
    B_out = 0;
    case (state)
         s0:begin
            if(B_in == 0)
                next_state = s1;
            else
                next_state = s3;
            B_out = 0;
            end
         s1:begin
                next_state = s2;
                B_out = 0;
            end
         s2:begin
                if(B_in == 0)
                    next_state = s1;
                else
                    next_state = s3;
                B_out = 1'b1;
            end
         s3:begin
                next_state = s0;
                B_out = 1'b1;
            end
    endcase
end
endmodule
