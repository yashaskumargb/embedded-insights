# To construct a bitfield mask based on a given start position (pos) and bitfield size (size), follow these steps:

## Step-by-Step Process

# Create a base mask of the desired size
 - Shift 1 left by size bits: 1 << size
 - Subtract 1 to set the lower size bits: (1 << size) - 1
  This produces a mask aligned to the least significant bits (LSBs).

# Shift the mask into position
 - Shift the base mask left by pos: ((1 << size) - 1) << pos
  This aligns the mask to the correct bitfield position.

# Syntax  
#define BIT_MASK(pos, size)   (((1U << (size)) - 1U) << (pos))
 - pos → starting bit position of the field.
 - size → number of bits in the field.
 - 1U ensures unsigned arithmetic (avoids sign-extension issues).
  Parentheses around parameters prevent operator precedence errors.

## Example
Create a mask for a bitfield of size = 4 starting at pos = 3:
unsigned int mask = BIT_MASK(3, 4);  
Step-by-step evaluation:  
  1U << 4 → 0b10000  
  (1U << 4) - 1U → 0b01111  
  (0b01111 << 3) → 0b01111000  
# Final mask: 0b01111000
