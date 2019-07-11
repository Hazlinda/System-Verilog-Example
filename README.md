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
      
 V C S   S i m u l a t i o n   R e p o r t 
 
      Colours :: Value of red 	 is = 0
      Colours :: Value of green 	 is = 1
      Colours :: Value of blue 	 is = 2
      Colours :: Value of yellow 	 is = 3
      Colours :: Value of white 	 is = 4
      Colours :: Value of black 	 is = 5
          
Example shows how to set other than default values to an enum

      module enum_data_type;
      //declaration
      enum {red=0, green, blue=4, yellow, white=10,black} Colours;
      
      //display members of Colours
            initial begin
            Colours = Colours.first;
    
                  for(int i=0; i<6; i++) begin
                        $display("Colours :: Value of %0s \t is = %0d", Colours.name, Colours);
                        Colours=Colours.next;
                  end
            end
      endmodule
 
  V C S   S i m u l a t i o n   R e p o r t 
  
      Colours :: Value of red 	 is = 0
      Colours :: Value of green 	 is = 1
      Colours :: Value of blue 	 is = 4
      Colours :: Value of yellow 	 is = 5
      Colours :: Value of white 	 is = 10
      Colours :: Value of black 	 is = 11
          
  Example shows declaring new data types using the enumerated type. 
  
          module enum_datatype;
          //declaration
          typedef enum {GOOD, BAD} pkt_type;
            pkt_type pkt_a;
            pkt_type pkt_b;
  
            initial begin
            pkt_a = GOOD;
            pkt_b = BAD;
    
            if(pkt_a == GOOD)
                  $display ("pkt_a is GOOD packet");
            else
                  $display ("pkt_a is BAD paket");
      
            if(pkt_b == GOOD)
                  $display ("pkt_b is GOOD packet");
            else 
                  $display ("pkt_b is BAD packet");
            end
          endmodule
          
 V C S   S i m u l a t i o n   R e p o r t
 
          pkt_a is GOOD packet
          pkt_b is BAD packet
           
           
  
  
      typedef enum {red=0, green, blue=4, yellow, white=10, black}Colors;
  
      enum{a,b,c,d,e,f,g} alphabets;
      colors first_set;
      colors second_set;
  
      initial begin
    
      first_set = first_set.first();
      $display("first_set first color is \t %0s, \t Value = %0d",first_set.name(),first_set);
      first_set = first_set.last();
      $display("first_set last color is \t %0s, \t Value = %0d",first_set.name(),first_set);
  
      second_set = first_set;
      $display("second_set color is \t %0s, \t Value = %0d", second_set.name(), second_set);
      second_set = second_set.prev(2);
      $display("second_set color is \t %0s, \t Value = %0d", second_set.name(),second_set);
      second_set = second_set.next(2);
      $display("second_set color is \t %0s, \t Value = %0d", second_set.name(),second_set);
           
           
