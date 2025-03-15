# DAY-46_100_DAYS_OF_RTL
//DETERMINNAT_3X3 MATRIIX

module determinant_3x3(
    input signed [7:0] a11, a12, a13,
    input signed [7:0] a21, a22, a23,
    input signed [7:0] a31, a32, a33,
    output reg signed [15:0] det
);
    always @(*) begin
        det =  a11 * (a22 * a33 - a23 * a32) 
             - a12 * (a21 * a33 - a23 * a31) 
             + a13 * (a21 * a32 - a22 * a31);
    end
endmodule
/////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////

module determinant_tb;
    reg signed [7:0] a11, a12, a13;
    reg signed [7:0] a21, a22, a23;
    reg signed [7:0] a31, a32, a33;
    wire signed [15:0] det;

    determinant_3x3 uut (a11, a12, a13, a21, a22, a23, a31, a32, a33, det);

    initial begin
        $monitor("Matrix:\n[%d %d %d]\n[%d %d %d]\n[%d %d %d]\nDeterminant = %d\n",
                 a11, a12, a13, a21, a22, a23, a31, a32, a33, det);
        
        // 🔹 Test Case 1
        a11 = 1; a12 = 2; a13 = 3;
        a21 = 4; a22 = 5; a23 = 6;
        a31 = 7; a32 = 8; a33 = 9;
        #10;

        // 🔹 Test Case 2
        a11 = 3; a12 = 1; a13 = 4;
        a21 = 1; a22 = 5; a23 = 9;
        a31 = 2; a32 = 6; a33 = 5;
        #10;

        // 🔹 Test Case 3
        a11 = 2; a12 = 0; a13 = 1;
        a21 = 3; a22 = 5; a23 = 2;
        a31 = 1; a32 = 4; a33 = 3;
        #10;

        $finish;
    end
endmodule
