# **Determining Padding Between Registers in Structure Layouts**

When defining peripheral register structures in embedded systems, it is often necessary to insert reserved fields (padding) to align subsequent registers correctly. This ensures that the structure layout matches the actual memory map of the hardware. The amount of padding required can be calculated if the addresses of two consecutive registers are known.

Step-by-Step Method

Let’s assume we have two registers

  Register 1 at address x (32-bit aligned)                                                                
  Register 2 at address y (32-bit aligned)
  
**The procedure to determine the padding is as follows**

- Calculate the byte difference Since Register 1 occupies 4 bytes (32 bits), the next available address after Register 1 is x + 4. The difference between Register 2’s address and this value gives the padding size in bytes:
    -  d=y-(x+4)
    
- Convert the difference to decimal The result d is typically in hexadecimal. Convert it to its decimal equivalent:
    -  z="decimal"(d)
    
- Convert bytes to words As registers are usually defined in word (4-byte) units, divide the decimal difference by 4:
    -  "Padding size"=z/4
This gives the number of reserved words required between the two registers.


**Example:** NVIC Peripheral
Consider the NVIC peripheral registers:
	NVIC_ISER at 0xE000E100UL
	NVIC_ICER at 0xE000E180UL
  
**Step 1: Calculate the difference**

  - d=(0xE000E180UL-(0xE000E100UL+4))=0x7C

**Step 2: Convert to decimal**

  - 0x7C=(7×16)+(12×1)=124" bytes" 

**Step 3: Convert to words**

  - 124/4=31" words" 

Thus, 31 reserved words must be inserted between NVIC_ISER and NVIC_ICER in the structure definition.
Conclusion

By subtracting the size of the first register and dividing the remaining gap by the word size, developers can precisely determine the amount of padding required. This method ensures that register structures in C accurately reflect the hardware memory map, avoiding misalignment and potential access errors.
For better visualization, please refer to below snapshots

<img width="975" height="261" alt="image" src="https://github.com/user-attachments/assets/bd980d37-d152-4209-a804-08cc8b99b7af" />
Figure 1. Snapshot of struct template for NVIC

<img width="975" height="322" alt="image" src="https://github.com/user-attachments/assets/3a758b41-6d5e-451c-834f-de5c8e3f7401" />
Figure 2. NVIC Register Memory Map with Reserved Padding

### **Note that, Not all registers of NVIC are included. This is just for example. So, I have considered I have only this much.**
