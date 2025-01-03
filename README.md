# ARITHMETIC-LOGIC-UNIT-ALU-_1





module ALU (
    input [7:0] A,
    input [7:0] B,
    input [2:0] Control,
    output reg [7:0] Result,
    output Zero,
    output Carry,
    output Negative
);
    reg C_out;
    always @(*) begin
        case (Control)
            3'b000: {C_out, Result} = A + B;       
            3'b001: {C_out, Result} = A - B;       
            3'b010: Result = A & B;              
            3'b011: Result = A | B;            
            3'b100: Result = ~A;                  
            default: Result = 8'b0;                
        endcase
    end

    assign Zero = (Result == 8'b0);
    assign Carry = C_out;
    assign Negative = Result[7];
endmodule
