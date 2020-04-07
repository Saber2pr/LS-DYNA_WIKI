Purpose: Set default control parameters for the Arbitrary Lagrange-Eulerian and Eulerian
calculations. See also *ALE_MULTI-MATERIAL_GROUP, *ALE_SMOOTHING, *INITIAL_
VOID_OPTION., and *SECTION_SOLID_ALE.

### Card Format

```card
Card1		1		2		3		4		5		6		7		8
Variable 	DCT 	NADV 	METH 	AFAC 	BFAC 	CFAC 	DFAC 	EFAC
Type 		I 		I 		I 		F		F		F		F		F
Default 	1		0		1		0		0		0		0		0

Card2		1		2		3		4		5		6		7		8
Variable 	START 	END 	AAFAC 	VFACT 	VLIMIT 	EBC
Type 		F		F		F		F		F		I
Default 	0 		1.0E+20 1 		1.0E-06 0.0 	0
```

### VARIABLE-DESCRIPTION

1. DCT

Default continuum treatment:
	EQ.1: Lagrangian (default),
	EQ.2: Eulerian,
	EQ.3: Arbitrary Lagrangian Eulerian,
	EQ.4: Eulerian Ambient.
	
---

2. NADV

Number of cycles between advections.

---

3. METH

Advection method:
	EQ.1: donor cell + HIS (first order accuracte),
	EQ.2: Van Leer + HIS (second order)

---

4. AFAC

ALE smoothing weight factor - Simple average:
	EQ.-1: turn smoothing off.

---
	
5. BFAC

ALE smoothing weight factor – Volume weighting

---

6. CFAC

ALE smoothing weight factor – Isoparametric

---

7. DFAC

ALE smoothing weight factor – Equipotential

8. EFAC

ALE smoothing weight factor – Equilibrium

---

9. START

Start time for ALE smoothing

---

10. END

End time for ALE smoothing

---

11. AAFAC

ALE advection factor (donor cell options, default=1.0)

---

12. VFACT

Volume fraction limit for stresses in single material and void formulation.
All stresses are set to zero for elements with lower volume fraction than VFACT.
	EQ.0.0: set to default 1.0E-06.

---
		
13. VLIMIT

Velocity limit. The time step is scaled down if the velocitiy exceed this limit.

---

14. EBC

Automatic Euler boundary condition
	EQ.0. off
	EQ.1. On with stick condition
	EQ.2. On with slip condition
This option, used for ALE and EULER formulations, defines velocity
boundary conditions for the user. Velocity boundary conditions are applied
to all nodes on free surfaces of an ALE or Eulerian material. For problems
where the normal velocity of the material at the boundary is zero such as
injection molding problems, the automatic boundary condition parameter is
set to 2. This will play the same role as the Nodal Single Point Constraint.
For EBC=1, the material velocity of all free surface nodes of ALE and
Euler material is set to zero.