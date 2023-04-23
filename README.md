Download Link: https://assignmentchef.com/product/solved-1082dsd-homework-2
<br>
<h1>Problem 1. 8-bit arithmetic logic unit (ALU)</h1>

In problem 1, you have to design an 8-bit arithmetic logic unit (ALU). The input and output ports are defined in Figure 1. The functions of ALU are defined in Table 1.

x [7:0]

y[7:0]

ctrl[3:0]

Figure 1

<h2>Table 1</h2>

<table width="503">

 <tbody>

  <tr>

   <td width="123">Control Signal(ctrl)</td>

   <td width="189">Description</td>

   <td width="191">Function</td>

  </tr>

  <tr>

   <td width="123">0000</td>

   <td width="189">Add(signed)</td>

   <td width="191">out = x + y</td>

  </tr>

  <tr>

   <td width="123">0001</td>

   <td width="189">Sub(signed)</td>

   <td width="191">out = x – y</td>

  </tr>

  <tr>

   <td width="123">0010</td>

   <td width="189">Bitwise And</td>

   <td width="191">out = and(x, y)</td>

  </tr>

  <tr>

   <td width="123">0011</td>

   <td width="189">Bitwise Or</td>

   <td width="191">out = or(x , y)</td>

  </tr>

  <tr>

   <td width="123">0100</td>

   <td width="189">Bitwise Not</td>

   <td width="191">out = not(x)</td>

  </tr>

  <tr>

   <td width="123">0101</td>

   <td width="189">Bitwise Xor</td>

   <td width="191">out = xor(x , y)</td>

  </tr>

  <tr>

   <td width="123">0110</td>

   <td width="189">Bitwise Nor</td>

   <td width="191">out = nor(x , y)</td>

  </tr>

  <tr>

   <td width="123">0111</td>

   <td width="189">Shift left logical variable</td>

   <td width="191">out = y &lt;&lt; x[2:0]</td>

  </tr>

  <tr>

   <td width="123">1000</td>

   <td width="189">Shift right logical variable</td>

   <td width="191">out = y &gt;&gt; x[2:0]</td>

  </tr>

  <tr>

   <td width="123">1001</td>

   <td width="189">Shift right arithmetic</td>

   <td width="191">out ={x[7],x[7:1]}</td>

  </tr>

  <tr>

   <td width="123">1010</td>

   <td width="189">Rotate left</td>

   <td width="191">out = {x[6:0] , x[7]}</td>

  </tr>

  <tr>

   <td width="123">1011</td>

   <td width="189">Rotate right</td>

   <td width="191">out = {x[0] , x[7:1]}</td>

  </tr>

  <tr>

   <td width="123">1100</td>

   <td width="189">Equal</td>

   <td width="191">out = (x==y)?1:0</td>

  </tr>

  <tr>

   <td width="123">1101</td>

   <td width="189">NOP (No operation)</td>

   <td width="191">out = 0</td>

  </tr>

  <tr>

   <td width="123">1110</td>

   <td width="189">NOP (No operation)</td>

   <td width="191">out = 0</td>

  </tr>

  <tr>

   <td width="123">1111</td>

   <td width="189">NOP (No operation)</td>

   <td width="191">out = 0</td>

  </tr>

 </tbody>

</table>

<ol>

 <li>“carry” only needs to be considered in ” <strong>Add(signed)</strong>”, ” <strong>Sub(signed)</strong>”. As for the other functions, “carry” can be arbitrary.</li>

 <li>carry is defined as the 9<sup>th</sup> bit of the result of 8-bit signed addition</li>

</ol>

e.g. x=1001_0110 and y=0010_1101 → x+y=1_1100_0011 → carry=1

(1)

Use Verilog to implement the <strong>RT</strong>-level (use <em>continuous assignment, <strong>assign</strong></em>) model of the 8-bit ALU. Modify the “alu_assign.v” file, which contains the module name and input/output ports. Use the given testbench, “alu_assign_tb.v” to verify your design. Use the following command for simulation:

<h3>                          ncverilog alu_assign_tb.v alu_assign.v +access+r</h3>

(2)

Use Verilog to implement the <strong>RT</strong>–level (use <em>procedural assignment, <strong>always</strong> block</em>) model of the 8-bit ALU. The input and output ports are the same as the previous one. Modify the “alu_always.v” file, and use the given testbench, “alu_always_tb.v” to verify your design. Use the following command for simulation:

<h3>                           ncverilog alu_always_tb.v alu_always.v +access+r</h3>

(3)

The given two testbenches “alu_assign_tb.v” “alu_always_tb.v” don’t check all the required functions of the ALU. You need to modify the two given testbenches and rename them to “alu_assign_tb2.v” and “alu_always_tb2.v”, respectively (They are the same but for different modules!). Use your modified testbenches to verify if all functions of your design are correct. Show the waveform results and describe how you verify the correctness in your report. If how you execute your testbench is different from 1-(1) and 1-(2), please provide a README so that TA can correctly test your design.

<h1>Problem 2. 8×8 Register File</h1>

A register file consists of a set of registers that can be read or written. There are 8 registers in this register file, and the width of each register is 8-bits. The input and output ports are described in Figure 2.

WEN RW RX RY

You must follow these specifications:

<ol>

 <li>I/O Port Functionality

  <ul>

   <li>busW: 8 bits input data bus</li>

   <li>busX、busY: 8 bits output data buses</li>

   <li>WEN: active high write enable (WEN==1)</li>

   <li>RW: select one of 8 registers to be written</li>

   <li>RX: select one of 8 registers to be read, output on busX</li>

   <li>RY: select one of 8 registers to be read, output on busY</li>

  </ul></li>

 <li>Register File (1) 8 registers.

  <ul>

   <li>$r0~$r7</li>

   <li>$r0=zero (constant zero, don’t care any write operation)</li>

  </ul></li>

 <li>Write Operation

  <ul>

   <li>The data on busW will be written into a specified register synchronously on positive edge of <strong>Clk </strong></li>

   <li>RW is the index of register to be written.</li>

  </ul></li>

 <li>Read Operation

  <ul>

   <li>The register file behaves as a combinational logic block when reading</li>

   <li>Read the data in the register file <strong>synchronously</strong></li>

  </ul></li>

</ol>

<ul>

 <li></li>

</ul>

Implement the register file in Verilog. Modify “register_file.v”, which contains the module name and input/output ports.

<ul>

 <li></li>

</ul>

Write the testbench (“register_file_tb.v”) to verify your design. Show the waveform results and describe how you verify the correctness in your report. Use the following command for simulation:

ncverilog register_file_tb.v register_file.v +access+r

<h1>Problem 3. Simple Calculator</h1>

Combine the previous two designs (ALU, Register File) into a simple calculator unit. You can use this unit to execute some simple programs. The input and output ports are defined in Figure 3. And there is a control signal “Sel” to select which data is input to ALU.

<ul>

 <li>When Sel = 0, DataIn is passed to port x of ALU.</li>

 <li>When Sel = 1, the data loaded to port x of ALU is from the register file.</li>

</ul>

Figure 3 You must define the following ports in your design:

<ol>

 <li>Input Port

  <ul>

   <li>Clk</li>

   <li>WEN</li>

   <li>RW</li>

   <li>RX</li>

   <li>RY</li>

   <li>DataIn</li>

   <li>Sel</li>

   <li>Ctrl</li>

  </ul></li>

 <li>Output Port

  <ul>

   <li>busY</li>

   <li>Carry</li>

  </ul></li>

</ol>

(1)

Use the previous two modules to implement the simple calculator unit (“simple_calculator.v”). After    finishing          the       calculator,       use     testbench (“simple_calculator_tb.v”) to test the correctness of your design. Use the following command for simulation:

ncverilog simple_calculator_tb.v simple_calculator.v +access+r

<h1>In your report, you should include the following parts</h1>

<ul>

 <li><strong>ALU</strong>: Screenshot the waveform result in nWave of alu_assign &amp; alu_always, describe how you verify the correctness.</li>

 <li><strong>8×8 Register File</strong>: Screenshot the waveform result in nWave of register_file, describe how you verify the correctness.</li>

 <li><strong>Describe what you found </strong>Write down what you found. Feel free to share your experience. (Ex: some mistakes you spend a lot of time, your environment, naming method) Anything you feel is special. The points depend on your answers!</li>

</ul>