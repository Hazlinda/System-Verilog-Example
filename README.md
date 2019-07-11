# System-Verilog-Example

# Behavioral Data Types:   

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

 V C S   S i m u l a t i o n   R e p o r t 
 
      string 1 s1 = Hazlinda
      string 2 s2 = Hi, I am Hazlinda
      string 3 s3 = 30
      string 4 s4 = I am , 30 years old 
          

# Enumeration Type [DataTypes] 

Example shows how to declare enum

      module enum_data_type;
      //declaration
      enum { red, green, blue, yellow, white, black} Colours;
  
      //display members of Colours
  
            initial begin
            Colours = Colours.first;
    
                  for (int i=0; i<6; i++) begin
                        $display ("Colours :: Value of %0s \t is = %0d", Colours.name, Colours);
                        Colours = Colours.next;
                  end
            end
      endmodule
