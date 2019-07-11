# System-Verilog-Example
Example code for string declaration


      module string_datatype;
      //declaration
      string s1 = "Hazlinda";
      string s2 = {"Hi, I am ","", s1};
      bit [31:0] b=30;
      string s3 = b ; //sets 30 to s3
      string s4 = {"I am "};
      string s5 = {" years old ", s5};
  
        initial begin
        //display values
        $display ("string 1 s1 = %0s", s1);
        $display ("string 2 s2 = %0s", s2);
        $display ("string 3 s3 = %0d", b);
        $display ("string 4 s4 = %0s, %0d",s4, s3, s5);
      end 
      endmodule
      
      
