# IMPORTANT:
The project is dead ! No longer supported. 

Consider using [opcodesDB](https://github.com/MahdiSafsafi/opcodesDB).

# Parsable-Instructions
List of all instructions found in *Intel* and *AMD* documentations, listed into ***XML files*** for easy parsing.
Each instruction in the XML file contains:

* Instruction mnemonic.
* Instruction arguments.
* Instruction opcode.
* Instruction opcode encoding.
* Instruction 64 bit mode support.
* Instruction 32 bit mode support.
* Instruction CPUID flags.
* Instruction operands encoding.
* Instruction description.

***NOTE***: Some fields listed above may not exists in other instructions.

For each **XML file** there is a **DTD file** associated which is used to ensure that the XML file follows the same rules for all XML files.

## XML files
- **raw.x86.Intel.AZ.xml**: Contains all instructions found in “Intel® 64 and IA-32 Architectures Software Developer Manuals volume 2”.
- **\*raw.x86.Intel.AVX512_r22.xml**: Contains all instructions found in “Intel® Architecture Instruction Set Extensions Programming Reference 319433-022”.
- **raw.x86.Intel.AVX512_r24.xml**: Contains all instructions found in “Intel® Architecture Instruction Set Extensions Programming Reference 319433-024”.
- **raw.x86.AMD.3DNow.xml**: Contains all instructions found in "AMD 3DNow! Technology Manual".
- **raw.x86.AMD.SSE5.xml**: Contains all instructions found in "AMD 128-Bit SSE5 Instruction Set".
- **raw.x86.AMD.XOP.xml**: Contains all instructions found in "AMD64 Architecture Programmers Manual Volume 6: 128-Bit and 256-Bit XOP and FMA4 Instructions".

\* means deprecated.

## KEY TO ABBREVIATIONS
  - **x32m** = 32-bit mode support.
  - **x64m** = 64-bit mode support.
  - **mnem** = Instruction Mnemonic.
  - **args** = Instruction Arguments.
  - **opc**  = Opcodes.
  - **openc** = Operand Encoding name.
  - **dscrp** = Description.
  - **oprndenc** = Instruction Operand Encoding.
  - **oprnd1** = Operand 1.
  - **oprnd2** = Operand 2.
  - **oprnd3** = Operand 3.
  - **oprnd4** = Operand 4.

***NOTE:*** FOR THE REST OF KEYS YOU SHOULD REFER TO INTEL/AMD DOCUMENTATIONS!

## Example
Here's a simple example of ADDPD instruction.
```
<common>
	<brief>ADDPD--Add Packed Double-Precision Floating-Point Values.</brief>
	<ins x32m="V" x64m="V">
		<mnem>ADDPD</mnem>
		<args>xmm1,xmm2/m128</args>
		<opc openc="RM">66 0F 58 /r</opc>
		<cpuid>
			<flag>SSE2</flag>
		</cpuid>
		<dscrp>Add packed double-precision floating-point values from xmm2/m128 to xmm1.</dscrp>
	</ins>
	<ins x32m="V" x64m="V">
		<mnem>VADDPD</mnem>
		<args>xmm1,xmm2,xmm3/m128</args>
		<opc openc="RVM">VEX.NDS.128.66.0F.WIG 58 /r</opc>
		<cpuid>
			<flag>AVX</flag>
		</cpuid>
		<dscrp>Add packed double-precision floating-point values from xmm3/mem to xmm2 and stores result in xmm1.</dscrp>
	</ins>
	<ins x32m="V" x64m="V">
		<mnem>VADDPD</mnem>
		<args>ymm1,ymm2,ymm3/m256</args>
		<opc openc="RVM">VEX.NDS.256.66.0F.WIG 58 /r</opc>
		<cpuid>
			<flag>AVX</flag>
		</cpuid>
		<dscrp>Add packed double-precision floating-point values from ymm3/mem to ymm2 and stores result in ymm1.</dscrp>
	</ins>
	<oprndenc openc="RM">
		<oprnd1>ModRM:reg(r,w)</oprnd1>
		<oprnd2>ModRM:r/m(r)</oprnd2>
		<oprnd3>NA</oprnd3>
		<oprnd4>NA</oprnd4>
	</oprndenc>
	<oprndenc openc="RVM">
		<oprnd1>ModRM:reg(w)</oprnd1>
		<oprnd2>VEX.vvvv(r)</oprnd2>
		<oprnd3>ModRM:r/m(r)</oprnd3>
		<oprnd4>NA</oprnd4>
	</oprndenc>
</common>
```

[1]:111
