# Lab 2

Reminder about how to create a project and begin editing a file. Note that your files should be named what we ask and you should always have your name and date in your verilog source files. This is the first step in "writing your own code" and helps me significantly as much of the grading I do is by hand. Having your name in the file makes it easier for me to get your grade into Canvas accurately (i.e. know whose code I am looking at so that when I click the rubric buttons I know I am in the right place.)

# Submission Details
Today's lab will be a pdf report again submitted to Canvas. Ideally you will submit 3 designs: a straight forward circuit from a boolean logic expression, a one-bit multiplexor, and a one-bit full adder. These latter two designs were a part of the in-class exercises and homework. Today's lab will be graded as follows: 
1. logic expression design (verilog, circuit screen capture, timing diagram screen capture): 5pts
2. multiplexor design(verilog, circuit screen capture, timing diagram screen capture): 2.5 pts
3. adder design(verilog, circuit screen capture, timing diagram screen capture): 2.5 pts

It is useful to finish these designs as they are a part of later projects and labs. It may be easier to turn in the verilog as a screen capture also to maintain the legibility and formatting.

## Project creation
Start the project
1. Use the `Windows` key to bring up the search bar for `Vivado`.
2. Start `Vivado`.
3. Under Quick Start, choose Create Project.
4. Hit Next to use the assist at creating projects Wizard.
5. Fill in the project name `lab2_combo` and file location.
6. Default is rtl project, which is what you want so just click Next.
7. Don't create a new file yet, just click Next.
8. No constraint file yet, so just click Next again.
9. Select the `parts` -> Category: `general purpose` -> Family: `Zynq-7000` -> `xc7z020clg484-3`.
10. Choose `Finish`.

# Individual Designs

# Boolean logic design

## Editing file
1. In the middle Sources window choose the plus tab.
2. Choose add or create design sources. Click `Next`.
4. Create new file by choosing the plus tab again, -> Create File. Name it `combo_eq`.
5. In the future you can specify parameters to your Module here, but for now lets make sure 
   to learn the whole structure of a Verilog program so you can write it yourself. Just click OK.
6. Click Yes.
7. Now you will notice in the Sources Window under Design Sources that the `combo_eq` file has been created.
8. Double click on the file and it will open a window on the right side.
9. Fill in the team member names under Engineer. As well as the other pertinent information.

-------
## Write Verilog for x = a'b'+ ab
1. Write structural verilog for the boolean logic expression `x = a'b' + ab`. File name should be `combo_eq`.
2. Create the 'schematic' and verify it is the correct circuit. Recall `RTL analysis` -> `Open Elaborated Design`
3. Edit your verilog if necessary.
4. Once your verilog and circuit are correct get screen captures for your report.
5. Using the procedures learned in a prior lab, force values to create a timing diagram that demonstrates the circuit is functioning correctly.
6. Create a screen capture of the timing diagram for your lab report.

____

# Multiplexor

## Multiplexor behavior (2 - 1)

A multiplexor is a digital circuit that can select one of `n` inputs (here `n` is `2`) and redirect that input to the output. The selection is done by the select input(`s`). To select one of several inputs, we need m select lines such that 2<sup>m</sup>=n. 

For example, if there are 8 input lines, we need 3 select bits to be able to select all input lines (2<sup>3</sup>=8).

In this lab, we will build a two to one multiplexor. Two inputs lines will go into the multiplexor and the output will be one of those inputs. A single bit will select which input will be reflected on the output. The two input lines should be labeled `d0` and `d1`. `d0` should be displayed on the output called `out` when the input labelled `select` is 0 and `d1` should be displayed when `select` is 1.

## Write Verilog for the one-bit (2-1) multiplexor
1. Write structural verilog for the one bit (2-1) multiplexor. Name this module `mux_2_1` and saved to `lab_2`.
2. Create the `schematic` and verify it is the correct circuit. Recall `RTL analysis` -> `Open Elaborated Design`
3. Edit your verilog if necessary.
4. Once your verilog and circuit are correct get screen captures for your report.
5. Using the procedures learned in a prior lab, force values to create a timing diagram that demonstrates the circuit is functioning correctly. Note there are 8 different possible input patters because there are three inputs. You only need to show the results for when the two inputs, `d0` and `d1`, are different.
6. Create a screen capture of the timing diagram for your lab report.
___

# Full Adder
---

## Full adder behavior 
A full adder circuit is the basic fundamental circuit that can perform addition or subtraction. It adds together two binary digits and a `carry_in` bit to produce the `sum` and `carry_out` digit. For example, 8 Full adders can be connected in series to make an 8 bit adder that will add two 8-bit numbers in either unsigned binary or two's complement representation.

A one-bit full adder will take in 3 one-bit inputs: two 1-bit inputs representing the digits to add and a one 1-bit `carry_in`. The full adder will have two outputs: a 1-bit `sum` and 1-bit `carry_out` that when used in conjunction with other one-bit adders will be the `carry_in` to the next more significant bit of the addition. 

## Write Verilog for the one-bit full adder
1. Write structural verilog for the one bit full adder. Name this module `full_adder` and saved to `lab_2`.
2. Create the 'schematic' and verify it is the correct circuit. Recall `RTL analysis` -> `Open Elaborated Design`
3. Edit your verilog if necessary.
4. Once your verilog and circuit are correct get screen captures for your report.
5. Using the procedures learned in a prior lab, force values to create a timing diagram that demonstrates the circuit is functioning correctly.
6. Create a screen capture of the timing diagram for your lab report.

____



