# 1.1 What is an Embedded System ?

An embedded system is a combination of computer hardware and software, either fixed in capability or programmable, designed for a specific function or functions within a larger system. Industrial machines, agricultural and process industry devices, automobiles, medical equipment, cameras, household appliances, airplanes, vending machines and toys, as well as mobile devices, are possible locations for an embedded system.

# 1.2 What Is a Target?

A target deploys MATLAB® and Simulink® designs to embedded hardware. With a target, you can prototype, verify, and deploy your application by generating processor-specific code, integrating real-time operating systems and device drivers, and profiling execution on your embedded hardware.

## 1.2.1 Hierarchy of Targets
You can develop a target by using an existing target. The existing target is then a reference target of the target being    developed. This guide shows you how to develop a target using a MathWorks® reference target.

Targets support hardware at the processor or board level. A hardware board includes one or more processors, and perhaps external memory, I/O devices, and other electronic components.

A target for a processor provides features that are related to the processor, such as assembly language optimizations. A target for a hardware board provides features related to the board, including its processor and any of its additional components, such as I/O device drivers.

Each hardware board includes a processor. When a target for a hardware board is developed, the target for the hardware board's processor is often used as the reference target.

For example, a BeagleBone Black board includes an ARM Cortex-A8 processor. Assume a target for BeagleBone Black boards supports the BeagleBone Black board, and a target for ARM Cortex-A processors supports the processor. Then you can develop a target for BeagleBone Black boards using the target for ARM Cortex-A processors as its reference target.

# 1.3 How do we compile and run a C program?

  We first create a C program using an editor and save the file as filename.c
    **$ vi filename.c**
 
  Then compile it using below command.
   **$ gcc –Wall filename.c –o filename**
 
  The option -Wall enables all compiler’s warning messages. This option is recommended to generate better code.
  The option -o is used to specify output file name. If we do not use this option, then an output file with name a.out is generated.

  After compilation executable is generated and we run the generated executable using below command.

   **$ ./filename** 
 
# 1.3.1 What goes inside the compilation process?
Compiler converts a C program into an executable. There are four phases for a C program to become an executable:

a. Pre-processing
b. Compilation
c. Assembly
d. Linking

By executing below command, We get the all intermediate files in the current directory along with the executable.

  **$gcc –Wall –save-temps filename.c –o filename**

### 1.3.1.1 Pre-processing
This is the first phase through which source code is passed. This phase include:

Removal of Comments
Expansion of Macros
Expansion of the included files.
The preprocessed output is stored in the filename.i. 

### 1.3.1.2 Compiling
The next step is to compile filename.i and produce an; intermediate compiled output file filename.s. This file is in assembly level instructions.

### 1.3.1.3 Assembly
In this phase the filename.s is taken as input and turned into filename.o by assembler. This file contain machine level instructions. At this phase, only existing code is converted into machine language, the function calls like printf() are not resolved.

### 1.3.1.4 Linking
This is the final phase in which all the linking of function calls with their definitions are done. Linker knows where all these functions are implemented. Linker does some extra work also, it adds some extra code to our program which is required when the program starts and ends. For example, there is a code which is required for setting up the environment like passing command line arguments. This task can be easily verified by using $size filename.o and $size filename. Through these commands, we know that how output file increases from an object file to an executable file. This is because of the extra code that linker adds with our program.

# 1.4 Static Linking and Static Libraries
is the result of the linker making copy of all used library functions to the executable file. Static Linking creates larger binary files, and need more space on disk and main memory. Examples of static libraries (libraries which are statically linked) are, .a files in Linux and .lib files in Windows.

# 1.4.1 Steps to create a static library
 ## 1. Create a C file that contains functions in your library.
   
   /* Filename: lib_mylib.c */
   
    #include <stdio.h> 
    
    void fun(void) 
    
    { 
    
    printf("fun() called from a static library"); 
    
    } 
    
    
   ## 2. Create a header file for the library
   
   /* Filename: lib_mylib.h */
   
    void fun(void); 
    
   ## 3. Compile library files. 
   
   **gcc -c lib_mylib.c -o lib_mylib.o** 
   
   ## 4. Create static library. This step is to bundle multiple object files in one static library (see ar for details). The output of this step is static library.
      
      **ar rcs lib_mylib.a lib_mylib.o** 
    
   ## 5. Now our static library is ready to use. 
   
   At this point we could just copy lib_mylib.a somewhere else to use it. For demo purposes, let us keep the library in the current directory.
    
   
   
