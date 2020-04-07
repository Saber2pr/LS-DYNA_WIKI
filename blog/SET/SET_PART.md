Available options include:
	LIST
	COLUMN
	LIST_GENERATE
The last option will generate a block of part ID’s between a starting part ID number and an ending
part ID number. An arbitrary number of blocks can be specified to define the part set.
Purpose: Define a set of parts with optional attributes. For the column option, see *AIRBAG or
*CONSTRAINED _RIGID_BODY_STOPPERS.

### Card Format

```card
Card1		1		2		3		4		5		6		7		8
Variable 	SID 	DA1 	DA2 	DA3 	DA4
Type 		I 		F		F		F		F
Default none 0.
```