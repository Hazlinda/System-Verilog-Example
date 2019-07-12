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
           
           
 Example shows how to use enumeration methods.  
  
      module enum_datatype;
      //declaration
      typedef enum { red=0, green, blue=4, yellow, white=10, black } colors;
   
      enum { a, b, c, d, e, f, g } alphabets;
      colors first_set;
      colors second_set;
   
          initial begin
     
            first_set = first_set.first();
            $display("First_set first color is \t %0s, \t Value = %0d", first_set.name(),first_set);
            first_set = first_set.last();
            $display("First_set last color is \t %0s, \t Value = %0d", first_set.name(),first_set);
 
            second_set = first_set;
            $display("Second_set color is \t %0s, \t Value = %0d", second_set.name(),second_set);
            second_set =second_set.prev(2);
            $display("Second_set color is \t %0s, \t Value = %0d", second_set.name(),second_set);
            second_set =second_set.next(2);
            $display("Second_set color is \t %0s, \t Value = %0d", second_set.name(),second_set);
   
            $display("Number of members in alphabets is \t %0d",alphabets.num());
            $display("Default First members in alphabets is \t %0s , \t value is %0d",alphabets.name(),alphabets);
            alphabets=alphabets.next;
            $display("Next members in alphabets is \t %0s , \t value is %0d",alphabets.name(),alphabets);
            alphabets=alphabets.last;
            $display("Last members in alphabets is \t %0s , \t value is %0d",alphabets.name(),alphabets);
            alphabets=alphabets.prev(3);
            $display("3rd members from last in alphabets is \t %0s , \t value is %0d",alphabets.name(),alphabets);
          end
      endmodule
      

 V C S   S i m u l a t i o n   R e p o r t 
 
      First_set first color is 	 red, 	 Value = 0
      First_set last color is 	 black, 	 Value = 11
      
      Second_set color is 	 black, 	 Value = 11
      Second_set color is 	 yellow, 	 Value = 5
      Second_set color is 	 black, 	 Value = 11
      
      Number of members in alphabets is 	 7
      Default First members in alphabets is 	 a , 	 value is 0
      Next members in alphabets is 	 b , 	 value is 1
      Last members in alphabets is 	 g , 	 value is 6
      3rd members from last in alphabets is 	 d , 	 value is 3
          
 # Class Data Types
 
A Class is a collection of data and a set of subroutines that operate on that data. The data in a class are referred to as class properties, and its subroutines are called methods.A Class is declared using the class...endclass keywords.
 
      class packet;
      // Properties
      bit [31:0] address;
      bit [31:0] data   ;
   
      // Method
      function new();
      $display("Inside new Function of packet");
      endfunction 
      endclass : packet
