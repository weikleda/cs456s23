# Lab 3

Reminder: Please put your name(s) in the Verilog code and label all parts of your lab report.

# Submission Details
Today's lab will be a pdf report again submitted to Canvas. Ideally you will submit 3 designs. The first three we will give you introducing an always block with and without a clock. You will build the circuit and run a simulation using a provided testbench, and the third will be your version of a D-write latch. Today's lab will be graded as follows: 
1. Always block example without clock (schematic, timing diagram): 3 pts
2. Always block example with clock (schematic, timing diagram): 3 pts
3. D latch with a write line (Verilog, schematic, timing diagram): 4 pts

It may be easier to turn in the verilog as a screen capture also to maintain the legibility and formatting.

## Project creation reminder
Start the project
1. Use the Windows key to bring up the search bar for Vivado.
2. Start Vivado.
3. Under Quick Start, choose Create Project.
4. Hit Next to use the assist at creating projects (Wizard).
5. Fill in the project name (lab3_seq) and file location.
6. Default is rtl project, which is what you want so just click Next.
7. Don't create a new file yet, just click Next.
8. No constraint file yet, so just click Next again.
9. Select the `parts` -> Category:-> `general purpose` -> Family: `Zynq-7000` -> `xc7z020clg484-3`.
10. Choose Finish.

# Individual Designs

## Description
In the homework you were asked to write a first attempt at Verilog for a D latch with a write line. The idea was to get you to write this using structural verilog only. Today in lab you will be given two designs using not only registers as in the homework, but an always block which allows you to create a sensitivity list. We will be talking about these more next week in class. This is an introduction and a way to get you to see the effect of registers on a circuit design.

For each of the two designs below, look at the Verilog code with your partner and discuss the new concepts. Pay particular attention to how the reg command is used and the always command. Within the parentheses of the always command is the "sensitivity list" - the signals that when changed will cause the commands inside to "happen". An always block is a form of behavioral verilog. We show you it in this setting to make clear how registers can give slightly different results.

## Always_block_no_clock
---

### Code

```verilog
module always_block_sense(
    input a_in, 
    output b_out,
    output c_out,
    output d_out
    );

    reg B;
    reg C;
    reg D;
    
    always @ (a_in) begin
    B = a_in;
    C = B;
    D = C;
    end
    
    
    assign b_out = B;
    assign c_out = C;
    assign d_out = D;

endmodule

```
### TestBench
A testbench is a way to run a simulation without typing in tcl commands. Create a new file using the testbench below to simulate the verilog code above.

```verilog

module always_no_clock;


    reg a;
    wire b_out, c_out, d_out;
    
       
    localparam time_step = 5;
    always_not_block_sense always_not_block_sense_tb(.a_in(a),  .b_out(b_out), .c_out(c_out), .d_out(d_out));
    
    initial
        begin
           
            
            a = 0;
            #time_step;
            
            a = 1;
            #time_step;     
            
            
            a = 1;
            #time_step;
                                
            
            a = 0;
            #time_step;
            
            a = 1;
            #time_step;
                       
                       
            a = 0;
            #time_step;
           
           
        end
    
endmodule

```


----

## Always_block_clock
Use the verilog code and the associated testbench below to create a schematic and timing diagram using a clock and an always block. Note the differences between the two schematics with and without a clock.

### Code

```verilog
module always_block(
        input clock,
        input a_in, 
        output b_out,
        output c_out,
        output d_out
    );
    
    reg B;
    reg C;
    reg D;

    always @ ( posedge clock ) begin
        B = a_in;
        C = B;
        D = C;
    end
    
    
    assign b_out = B;
    assign c_out = C;
    assign d_out = D;
endmodule

```

### TestBench

```verilog
module always_clock;

    reg a, clock;
    wire b_out, c_out, d_out;
    
       
    localparam time_step = 5;
    always_block always_block_tb(.clock(clock), .a_in(a),  .b_out(b_out), .c_out(c_out), .d_out(d_out));
    

    
    initial
        begin
           
            clock = 0;
            a = 0;
            #time_step;
            
            clock = 1;
            a = 1;
            #time_step;
            
            
            clock = 0;
            a = 1;
            #time_step;
                       
                       
            clock = 1;
            a = 0;
            #time_step;
            
            
            clock = 0;
            a = 0;
            #time_step;
            
            
            clock = 1;
            a = 1;
            #time_step;
                       
                       
           
           
        end
    
    
endmodule

```


----
## D-Write Latch
Using what you learned, write the Verilog for a D-write latch using structural Verilog. Your module should have a clock, write line, and a d input as inputs and a single output, q. You do not need to use an always block. If time, try writing one with and without an always block. You may use a testbench to run your simulation or use forcing tcl commands. Create a schematic and a timing diagram from your verilog.
