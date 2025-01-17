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
opcode: 0010011  
rd: a1 = x11 = 01011  
funct3: 000   
rs1: x0 = 00000  
imm[11:0]: 000000011001  
Binary: 00000001100100000000010010010011      

#### 4. sd ra, 8(sp)  
opcode: 0100011  
funct3: 011   
rs1: sp = x2 = 00010  
rs2: ra = x1 = 00001  
imm[11:5]: 0000000 (upper 7 bits of 8)  
imm[4:0]: 01000 (lower 5 bits of 8)  
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

#### 8. auipc gp, 0x13  
Type: U-type  
Opcode: 0010111  
Immediate: 000000000000000000010011  
Destination Register (rd): 01010 (gp, x10)  
Final Binary Representation: 0000000000000000000100110101001010111  

#### 9. beqz a5, 100f8 <register_fini+0x18>  
Type: B-type  
Opcode: 1100011 (BEQ)  
Source Register 1 (rs1): 01010 (a5, x10)  
Source Register 2 (rs2): 00000 (x0)  
Immediate: 0000000000000110  
Final Binary Representation: 00000000000001100000001010000100011

  
#### 10. sub a2, a2, a0  
Type: R-type  
Opcode: 0110011  
Source Register 1 (rs1): 01000 (a2, x8)  
Source Register 2 (rs2): 01000 (a0, x10)  
Destination Register (rd): 01001 (a2)  
Funct3: 000  
Funct7: 0100000  
Final Binary Representation: 01000000100001000000010010110011  


#### 11. lw a0, 0(sp)  
Type: I-type  
Opcode: 0000011  
Destination Register (rd): 01000 (a0, x10)  
Immediate: 000000000000  
Source Register 1 (rs1): 01010 (sp, x2)  
Funct3: 010  
Final Binary Representation: 00000000000001010010010000000011  
