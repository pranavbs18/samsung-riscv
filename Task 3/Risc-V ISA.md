#### 1. lui a2, 0x1
Type: U-Type.  
opcode: 0110111 (for lui)  
rd: a2 = x12 = 01100  
imm[31:12]: 0x1 = 0000 0000 0000 0001  
Binary: 00000000000000000001011000110111  

#### 2. addi a2, a2, 954
imm[11:0]: 954 = 0011 1011 1010  
rs1: a2 = x12 = 01100  
rd: a2 = x12 = 01100  
funct3: 000   
opcode: 0010011  
Binary: 00111011101001100000011000010011  

#### 3. li a1, 100  
Expansion: addi a1, x0, 100  
Binary: 000000011001 00000 000 01001 0010011  

#### 4. sd ra, 8(sp)  
Binary: 00000000000100010011010000100011  

#### 5. jal ra, 1040c
Type: J-Type.  
rd: ra = x1 = 00001  
opcode: 1101111  
Placeholder  0x340000ef  

#### 6. ld ra, 8(sp)
Type: I-Type.  
opcode: 0000011   
funct3: 011  
rs1: sp = x2 = 00010  
rd: ra = x1 = 00001  
imm[11:0]: 8 = 0000 0000 1000  
Binary: 000000000100000010011000010000011  

#### 7. ret
opcode: 1100111   
funct3: 000   
rs1: ra = x1 = 00001  
rd: x0 = 00000    
imm[11:0]: 0 = 0000 0000 0000  
Binary: 00000000000000001000000001100111
