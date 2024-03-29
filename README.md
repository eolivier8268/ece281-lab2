# Lab 2: Seven Segment Display Decoder

VHDL for ECE 281 [Lab 2](https://usafa-ece.github.io/ece281-book/lab/lab2.html)

Targeted toward Digilent Basys3. Make sure to install the [board files](https://github.com/Xilinx/XilinxBoardStore/tree/2018.2/boards/Digilent/basys3).

Tested on Windows 11.

---

## Build the project

Follow the instructions to [Create a new Vivado Project](https://usafa-ece.github.io/ece281-book/appendix/vivado.html#create-a-new-vivado-project). Suggested name is binaryHexDisp.

Then add all the files in `src/hdl/` to the project, as described [here](https://usafa-ece.github.io/ece281-book/appendix/vivado.html#manually-add-files-to-vivado-project)

## GitHub Actions Testbench

The workflow uses the [setup-ghdl-ci](https://github.com/ghdl/setup-ghdl-ci) GitHub action
to run a *nightly* build of [GHDL](https://ghdl.github.io/ghdl/).

First, the workflow uses GHDL to **analyze** all `.vhd` files in `src/hdl/`.

Then it **elaborates** the *any* entity with the name `*_tb`. In this case, that is `helloled_tb`.

Finally, the workflow **runs** the simulation. If successful then it will quietly exit with a `0` code.
If any of the `assert` statements fail **with** `severity failure` then GHDL will cease the simulation and exit with non-zero code; this will also cause the workflow to fail.
Assert statements of other severity levels will be reported, but not fail the workflow.

## Results

The implementation of the seven segment display was written and tested.  
The output waveform below matched the pre-lab.  
![waveform from test bench](./img/waveform_7SD_testbench.png)  
![inputs and outputs from pre-lab](./img/prelab-IO-table.png)  

The top-level design was created and tested on the basys3 board.   
The design ran successfully, and a demo video was uploaded in Teams. 

## Documentation Statement

I watched the code-walk of ICE3 uploaded by Capt Yarbrough to get a better understanding of how VHDL works.  
C3C Cavan Cook and I also talked through the difference between entities and components and multi-level design.  
My code already worked by this time so I did not change anything based on the video or my discussion with C3C Cook.  