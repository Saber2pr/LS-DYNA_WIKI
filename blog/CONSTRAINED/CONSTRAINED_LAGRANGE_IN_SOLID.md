### Purpose: 

Couple a Lagrangian mesh (slave) of shells, solids or beams to the material points of an
Eulerian mesh (master). This option may also be used to model rebar in concrete or tire cords in
rubber. The slave part or slave part set is coupled to the master part or master part set.

> Note: For RIGID slave PARTS a penalty coupling method must be used, see option CTYPE below.

### Card Format

```card
Card1		1		2		3		4		5		6		7		8
Variable 	SLAVE 	MASTER 	SSTYP 	MSTYP 	NQUAD 	CTYPE 	DIREC 	MCOUP
Type 		I		I		I		I		I		I		I		I
Default 	none 	none 	0		0		0		2		1		0
```

```card
Card2		1		2		3		4		5		6		7		8
Variable 	START 	END 	PFAC 	FRIC 	FRCMIN 	NORM
Type 		F		F		F		F		F		I
Default 	0 		1.0E10 	0.1 	0.0 	0.5 	0
```

```card
Card3		1		2		3		4		5		6		7		8
Variable 	CQ 		HMIN 	HMAX
Type 		F 		F 		F
Default 	0.0 	none 	none
```

### VARIABLE-DESCRIPTION

1. SLAVE:

Part, part set ID or Segment set ID of slaves see *PART , *SET_PART or
*SET_SEGMENT.

---

2. MASTER

Part or part set ID of master solid elements, see *PART or *SET_PART.

---

3. SSTYP 

Slave type:
	EQ.0: part set ID,
	EQ.1: part ID.
	EQ.2: segment set ID

---
	
4. MSTYP 

Master type:
	EQ.0: part set ID,
	EQ.1: part ID.

---

5. NQUAD 

Quadratue rule for coupling slaves to solids.
	EQ.0: at nodes only,
	EQ.n: use a rectangular grid of n*n points,
	EQ.-n: at nodes and a rectangular grid of n*n points.

---

6. CTYPE 

Coupling type:
	EQ.1: constrained acceleration,
	EQ.2: constrained acceleration and velocity (default),
	EQ.3: constrained acceleration and velocity, normal
	direction only,
	EQ.4: penalty coupling (Shell Elements),
	EQ.5: penalty coupling with erosion (Solid Elements).

---

7. DIREC 

Coupling direction (CTYPE 4 and 5).
	EQ.1: normal direction, compression and tension (default),
	EQ.2: normal direction, compression only,
	EQ.3: all directions.

---

8. MCOUP 

Multi-material option (CTYPE 4 and 5).
	EQ.0: couple with all multi-material groups,
	EQ.1: couple with material with highest density.

---

9. START 

Start time for coupling.

---

10. END 

End time for coupling.

---

11. PFAC 

Penalty factor (CTYPE 4 and 5 only).

---

12. FRIC 

Coefficient of friction (DIREC 2 only).

---

13. FRCMIN 

Minimum volume fraction to activate coupling (MCOUP=1)

---

14. NORM 

Shell and segment normal orientation:
	EQ.0: right hand rule (default),
	EQ.1: left hand rule.

---

15. CQ 

Heat transfer coefficeint, Cq .

---

16. HMIN

Minimum air gap in heat transfer, hmin .

---

17. PFAC 

Maximum air gap in heat transfer, hmax . There is no heat transfer above this value.

