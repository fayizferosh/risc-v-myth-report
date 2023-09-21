![RISC-V_Pipelined_Core_using_TL-Verilog](https://github.com/fayizferosh/risc-v-myth-report/assets/63997454/5e9b5052-394a-4269-b730-8988585c94fd)
# RISC-V Pipelined Core using TL-Verilog

![Static Badge](https://img.shields.io/badge/OS-linux-orange)
![Static Badge](https://img.shields.io/badge/Tools-gcc-navy)
![Static Badge](https://img.shields.io/badge/languages-C%2C_TL--Verilog-crimson)
![GitHub last commit](https://img.shields.io/github/last-commit/fayizferosh/risc-v-myth-report)
![GitHub language count](https://img.shields.io/github/languages/count/fayizferosh/risc-v-myth-report)
![GitHub top language](https://img.shields.io/github/languages/top/fayizferosh/risc-v-myth-report)
![GitHub repo size](https://img.shields.io/github/repo-size/fayizferosh/risc-v-myth-report)
![GitHub code size in bytes](https://img.shields.io/github/languages/code-size/fayizferosh/risc-v-myth-report)
![GitHub repo file count (file type)](https://img.shields.io/github/directory-file-count/fayizferosh/risc-v-myth-report)
<!---
Comments
-->

> A beginner level 5-day workshop on “RISC-V based MYTH” (Microprocessor for You in Thirty Hours). In the workshop the following topics are discussed namely RISC-V specs, RISC-V software, how to implement RISC-V basic specs using TL-Verilog, simulate your own RISC-V core. The final objective by day 5 is to write RTL and build RISC-V core on my own.

A C program which has to be run on a specific hardware layout which is the interior of a chip in your laptop, there is certain flow to be followed. Initially, this particular C program is compiled in it's assembly language program which is nothing but RISC-V ISA (Reduced Instruction Set Compting - V Intruction Set Architecture). Following this, the assembly language program is then converted to machine language program which is the binary language logic 0 and 1 which is understood by the hardware of the computer. Directly after this, we've to implement this RISC-V specification using some RTL (a Hardware Description Language). Finally, from the RTL to Layout it is a standard PnR or RTL to GDSII flow.

![Screenshot (278)](https://github.com/fayizferosh/risc-v-myth-report/assets/63997454/7dc4601a-e386-48e5-9d1f-7fa5b47ca0ba)

For an application software to be run on a hardware there are several processes taking place. To begin with, the apps enters into a block called system software and it converts the application program to binary language. There are various layers in system software in which the major layers or components are OS (Operating System), Compiler and Assembler. At first the OS outputs are small function in C, C++, VB or Java language which are taken by the respective compiler and converted into instructions and the syntax of these instructions varies with the hardware architecture on which the system is implemented. Then, the job of the assembler is to take these instructions and convert it into it's binary format which is basically called as a machine language program. Finally, this binary language is fed to the hardware and it understands the specific functions it has to perform based on the binary code it receives.

![Screenshot (279)](https://github.com/fayizferosh/risc-v-myth-report/assets/63997454/19e8b634-f209-41a6-928d-6fba66f5b177)

For example, if we take a stopwatch app on RISC-V core, then the output of the OS could be a small C function which enters into the compiler and we get output RISC-V instructions following this, the output of the assembler will be the binary code which enters into your chip layout.

![Screenshot (280)](https://github.com/fayizferosh/risc-v-myth-report/assets/63997454/7d4570ca-82a6-4abe-81d2-067ebb9b2c15)

For the above stopwatch the following are the input and output of the compiler and assembler.

![Screenshot (281)](https://github.com/fayizferosh/risc-v-myth-report/assets/63997454/d7b7fd1b-21ee-46b7-9a91-8314bd753a51)

The output of the compiler are instructions and the output of the assembler is the binary pattern. Now, we need some RTL (a Hardware Description Language) which understands and implements the particular instructions. Then, this RTL is synthesised into a netlist in form of gates which is fabricated into the chip through a physical design implementation.

![Screenshot (282)](https://github.com/fayizferosh/risc-v-myth-report/assets/63997454/e349cb06-45e3-4ae4-b85f-9020a0a62737)

There are mainly 3 different parts in this course. They are:
1. RISC-V ISA
2. RTL and synthesis of RISC-V based CPU core - picorv32
3. Physical design implementation of picorv32

![Screenshot (283)](https://github.com/fayizferosh/risc-v-myth-report/assets/63997454/832f0ea6-2d60-4d9a-937c-a2dedd5f8cac)

## Day 1 - Introduction to RISC-V ISA and GNU compiler toolchain (20/09/2023)

Contents:
1. Introduction to RISC-V basic keywords
2. Labwork for RISC-V software toolchain
3. Integer number representation
4. Signed and unsigned arithmetic operations

## Part 1a - RISC-V ISA

The following are basic C program which will do integer addition, multiplication and division.

![Screenshot (284)](https://github.com/fayizferosh/risc-v-myth-report/assets/63997454/0edd3353-be8d-4bf5-93cc-b5af7654ed71)

And these are the output of the compiler for these codes which is nothing but a set of RISC-V instructions which perform the integer addition, multiplication and division.

![Screenshot (285)](https://github.com/fayizferosh/risc-v-myth-report/assets/63997454/f8926f6b-18ae-4309-8021-9d3a194b463d)

The following are the different sets of instructions which form the RISC-V ISA:

![Screenshot (286)](https://github.com/fayizferosh/risc-v-myth-report/assets/63997454/ba91e6c3-a0e5-4e26-a7b3-977b6d993441)
![Screenshot (287)](https://github.com/fayizferosh/risc-v-myth-report/assets/63997454/7dc0afc0-3d44-4669-8694-43e4d48114e0)
![Screenshot (288)](https://github.com/fayizferosh/risc-v-myth-report/assets/63997454/448260e4-b3f9-46ce-a9fe-5816733d5ed7)

The following are basic C program which will do floating point addition, multiplication and division.

![Screenshot (289)](https://github.com/fayizferosh/risc-v-myth-report/assets/63997454/bc6b7441-9d00-42f4-b095-05bc511e497f)

And these are the output of the compiler for these codes which is nothing but a set of RISC-V instructions which perform the floating point addition, multiplication and division.

![Screenshot (290)](https://github.com/fayizferosh/risc-v-myth-report/assets/63997454/253d30fd-f57d-48d2-8400-b6c1d0123449)

The following are the rest of the different sets of instructions which form the RISC-V ISA:

![Screenshot (291)](https://github.com/fayizferosh/risc-v-myth-report/assets/63997454/34b6d5a1-75ba-4171-810e-ecfa2ad8c386)

If we look into all the instruction over here these are some interface with which the user can access the RISC-V registers.

![Screenshot (292)](https://github.com/fayizferosh/risc-v-myth-report/assets/63997454/54324034-1544-4369-9d32-9e5c5e87c2e1)

In the following highlighted instructions there are some data transfer happening between memory, stack pointer or register.

![Screenshot (293)](https://github.com/fayizferosh/risc-v-myth-report/assets/63997454/bc831159-437b-47c3-8725-738136f6cfd3)

### Lab 1

C Program *sum1ton.c*:

```C
#include<stdio.h>
int main()
{
    int i,sum=0,n=9;
    for(i=1;i<=n;i++)
    {
        sum+=i;
    }
    printf("The sum of numbers from 1 to %d is %d\n", n, sum);
    return 0;
}
```

Commands to compile & execute and generate output of C program:

```bash
# Compiling the code
gcc sum1ton.c
# Executing the code
./a.out
```

**Screenshot**

![Screenshot from 2023-09-21 15-47-09](https://github.com/fayizferosh/risc-v-myth-report/assets/63997454/28bf2d71-ea12-4e66-9c35-2599045cd8f8)

Commands to compile & execute the same C program using RISC-V simulator:

Details regarding optimization options -O1 & -Ofast can be found [here](https://gcc.gnu.org/onlinedocs/gcc/Optimize-Options.html).

Details regarding rest of the options -mabi, -march and so on can be found [here](https://gcc.gnu.org/onlinedocs/gcc/RISC-V-Options.html).

```bash
# Compiling code on RISC-V simulator in -O1 optimization
riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o sum1ton_O1.o sum1ton.c
# Disassembling compiled code
riscv64-unknown-elf-objdump -d sum1ton_O1.o > sum1ton_O1_d.txt
# Compiling code on RISC-V simulator in -Ofast optimization
riscv64-unknown-elf-gcc -Ofast -mabi=lp64 -march=rv64i -o sum1ton_Ofast.o sum1ton.c
# Disassembling compiled code
riscv64-unknown-elf-objdump -d sum1ton_Ofast.o > sum1ton_Ofast_d.txt
```

**Screenshots**

![Screenshot from 2023-09-21 15-53-36](https://github.com/fayizferosh/risc-v-myth-report/assets/63997454/6e0951cd-37aa-40d5-b842-a96e31cca153)

**-O1 and -Ofast optimizations instruction count in main() function**

![Screenshot from 2023-09-21 15-59-04](https://github.com/fayizferosh/risc-v-myth-report/assets/63997454/8e98c586-6ad6-453c-80fb-f5aca9f7e07b)
![Screenshot from 2023-09-21 16-01-49](https://github.com/fayizferosh/risc-v-myth-report/assets/63997454/434f32c8-5300-4e1d-9699-d65ae9c6d588)


```bash
# Executing the code
spike pk sum1ton_O1.o
# To debug type
spike -d pk sum1ton_O1.o
```
```bash
# In debug mode
# Run until program counter "10184"
(spike) until pc 0 10184
# Display value of stack pointer "sp"
(spike) reg 0 sp
# Just press "Enter" to run the next instruction
(spike)
# Checking stack pointer "sp" value again
(spike) reg 0 sp
# Just press "Enter" to run the next instruction
(spike)
(spike)
(spike)
# Display value of register "a0"
(spike) reg 0 a0
# Just press "Enter" to run the next instruction
(spike)
# Checking register "a0" value again
(spike) reg 0 a0
# Just press "Enter" to run the next instruction
(spike)
# Checking register "a0" value again
(spike) reg 0 a0
# Exiting debug mode
(spike) q
```

**Screenshot**

![Screenshot from 2023-09-21 17-05-55](https://github.com/fayizferosh/risc-v-myth-report/assets/63997454/56001275-49b5-4b08-8a69-8d019a10c739)

```bash
# Executing the code
spike pk sum1ton_Ofast.o
# To debug type
spike -d pk sum1ton_Ofast.o
```
```bash
# In debug mode
# Run until program counter "100b0"
(spike) until pc 0 100b0
# Display value of register "a0"
(spike) reg 0 a0
# Just press "Enter" to run the next instruction
(spike)
# Checking register "a0" value again
(spike) reg 0 a0
# Display value of stack pointer "sp"
(spike) reg 0 sp
# Just press "Enter" to run the next instruction
(spike)
# Checking stack pointer "sp" value again
(spike) reg 0 sp
# Just press "Enter" to run the next instruction
(spike)
(spike)
# Display value of register "a0"
(spike) reg 0 a0
# Just press "Enter" to run the next instruction
(spike)
# Checking register "a0" value again
(spike) reg 0 a0
# Exiting debug mode
(spike) q
```

**Screenshot**

![Screenshot from 2023-09-21 17-19-41](https://github.com/fayizferosh/risc-v-myth-report/assets/63997454/ff6374e0-6d4e-4db5-a2d2-4d44d6c5235e)


***lui* command**

![Screenshot (294)](https://github.com/fayizferosh/risc-v-myth-report/assets/63997454/1c4648d0-1583-4e24-ab0d-c78a17400c5f)

***addi* command**

![Screenshot (296)](https://github.com/fayizferosh/risc-v-myth-report/assets/63997454/2fce31ac-2214-42c3-a97f-2cb43127302b)

**Important Terms**

![Screenshot (297)](https://github.com/fayizferosh/risc-v-myth-report/assets/63997454/bff11b16-04a5-4326-9d38-d89dcb6f8447)

**Maximum amount of numbers that can be expressed in 64bit**

![Screenshot (299)](https://github.com/fayizferosh/risc-v-myth-report/assets/63997454/60cdd2dd-5f3d-4ae0-96e6-37df0c2546fb)

**Unsigned 64bit limits**

![Screenshot (300)](https://github.com/fayizferosh/risc-v-myth-report/assets/63997454/46e95ff8-57e2-43e5-bc5a-eefc637366e9)

**Signed postive representation and signed negative in two's compliment representation**

![Screenshot (301)](https://github.com/fayizferosh/risc-v-myth-report/assets/63997454/04b6f7d6-ea3e-4fe3-86b3-f4bf56683e0b)
![Screenshot (302)](https://github.com/fayizferosh/risc-v-myth-report/assets/63997454/496d4bef-014e-4c35-9778-fe7177636a26)
![Screenshot (303)](https://github.com/fayizferosh/risc-v-myth-report/assets/63997454/4fba20b7-1195-4876-83fb-dc761b077ed3)
![Screenshot (304)](https://github.com/fayizferosh/risc-v-myth-report/assets/63997454/9e6bd23a-2f93-493f-a733-b1c5af359dda)
![Screenshot (305)](https://github.com/fayizferosh/risc-v-myth-report/assets/63997454/d051d15d-3843-4b23-88e6-5ad7a15755d6)
![Screenshot (306)](https://github.com/fayizferosh/risc-v-myth-report/assets/63997454/4786b124-d725-4856-a6af-51b1969d12c1)

**Signed 64bit limits**

![Screenshot (308)](https://github.com/fayizferosh/risc-v-myth-report/assets/63997454/1b1050d0-2e92-45b8-b3a9-291d1ab1b63d)
![Screenshot (309)](https://github.com/fayizferosh/risc-v-myth-report/assets/63997454/054d1483-9558-428a-9ec1-8864f27d18af)

### Lab 2

C Program *unshighlow.c*:

```C
#include<stdio.h>
#include<math.h>

int main()
{
    unsigned long long int max = (unsigned long long int)(pow(2,64)-1); 
    unsigned long long int maxover = (unsigned long long int)(pow(2,127));
    unsigned long long int min = (unsigned long long int)(0);
    unsigned long long int minover = (unsigned long long int)(pow(2,64)*-1);
    printf("Highest number represented by unsigned long long int is %llu which is calculated by (2^64 - 1)\n", max);
    printf("Proving by overflowing above limit (2^127) value of variable still is %llu\n", maxover);
    printf("Lowest number represented by unsigned long long int is %llu\n", min);
    printf("Proving by overflowing below limit (2^64 * -1) value of variable still is %llu\n", minover);
    return 0;
}
```

Commands to compile & execute the same C program using RISC-V simulator:

```bash
# Compiling code on RISC-V simulator in -Ofast optimization
riscv64-unknown-elf-gcc -Ofast -mabi=lp64 -march=rv64i -o unshighlow_Ofast.o unshighlow.c
# Executing the code
spike pk unshighlow_Ofast.o
```

**Screenshot**

![Screenshot from 2023-09-21 17-33-21](https://github.com/fayizferosh/risc-v-myth-report/assets/63997454/d58cbe25-231e-4abb-8b6a-a664dec8f20c)

C Program *signhighlow.c*:

```C
#include<stdio.h>
#include<math.h>

int main()
{
    long long int max = (long long int)(pow(2,63)-1); 
    long long int maxover = (long long int)(pow(2,127));
    long long int min = (long long int)(pow(2,63)*-1);
    long long int minover = (long long int)(pow(2,127)*-1);
    printf("Highest positive number represented by signed long long int is %lld which is calculated by (2^63 - 1)\n", max);
    printf("Proving by overflowing above limit (2^127) value of variable still is %lld\n", maxover);
    printf("Lowest negative number represented by signed long long int is %lld which is calculated by (2^63 * -1)\n", min);
    printf("Proving by overflowing below limit (2^127 * -1) value of variable still is %lld\n", minover);
    return 0;
}
```

Commands to compile & execute the same C program using RISC-V simulator:

```bash
# Compiling code on RISC-V simulator in -Ofast optimization
riscv64-unknown-elf-gcc -Ofast -mabi=lp64 -march=rv64i -o signhighlow_Ofast.o signhighlow.c
# Executing the code
spike pk signhighlow_Ofast.o
```

**Screenshot**

![Screenshot from 2023-09-21 17-37-11](https://github.com/fayizferosh/risc-v-myth-report/assets/63997454/161e5477-2cc5-4413-b786-ef5fe13b7b06)

## Day 2 - Introduction to ABI and basic verification flow (21/09/2023)

Contents:
1. Application Binary interface (ABI)
2. Lab work using ABI function calls
3. Basic verification flow using iverilog
