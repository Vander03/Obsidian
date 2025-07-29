**didnt end up finishing**
![[Pasted image 20250322163903.png|500]]
## 1 Desktop Application Development
![[Pasted image 20250322164850.png|500]]
## 2 Embedded Application Development
![[Pasted image 20250322165052.png|500]]
 
## 3 Pre-Processing
Most # keywords are evaluated at this stage, including `#include`, `#ifndef`, `#define`, and `#includes` are resolved by copying header files into source files.
This step is technically part of the **compilation** process.
## 4 Compilation/Assembler
Each source file is eventually compiled/assembled into object files. High level languages are first compiled into assembly. Involves lexical analyser, syntax analyser, code optimiser, code generator and error handler.
The assembly code is then turned into instructions or machine code within relocatable object files (.o)

### 4.1 Concerns with Compilation
1 line of code isn't always 1 line of assembly, and as such can be interrupted.
Say after data was put into r3, an interrupt happens that operates in r3 and changes the variable that is then operated upon after. A line of code is not **atomic**.

We can make sure its protected by using **volatile**.
## 5 Linking + Locating
All object files are linked to produce a single object file (relocatable file)
Merges code and data sections by linking references across different .o files. Produces a single relocatable file.
When linking `__attribute__` can be used to define a section that needs to start at 0 in flash memory, demonstrated in `startup_gcc.c`

![[Pasted image 20250323201950.png]]

### 5.1 Linker Scripts (.ld)
![[Pasted image 20250323203853.png|]]


## 6 Relocation
Physical memory addresses must be assigned to the relative offsets within relocatable file.
This step produces the final binary image ready to run on the microcontroller

## 7 Build Flags
![[Pasted image 20250322181735.png|600]]
![[Pasted image 20250322181801.png|500]]

## 8 Object File
Roadmap that provides instructions to the linker and locator on how to produce the binary image. Follows after the compiler stage.

Three types: relocatable, executable, shared object file
Common formats: Common Object File Format (COFF), Executable and Linkable Format (ELF)
Contains header describing sections (sections are the smallest indivisible units that an be processed)

### 8.1 Sections
![[Pasted image 20250323201512.png]]


![[Pasted image 20250323203230.png]]