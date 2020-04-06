### *SECTION_SOLID_{OPTION}

Options include:
	<BLANK>
	ALE
such that the keyword cards appear:
	*SECTION_SOLID
	*SECTION_SOLID_ALE

> Purpose: Define section properties for solid continuum and fluid elements.

### Card 1 define for all options

```card
Card1		1		2		3		4		5		6		7		8
Variable	SECID	ELFORM	AET
Type		I		I		I
Remark				1, 2
```

### Card 2 define only for the ALE option.
> Also see *ALE_SMOOTHING for the smoothing definition

```card
Card2		1		2		3		4		5		6		7		8
Variable 	AFAC	BFAC 	CFAC 	DFAC 	START 	END 	AAFAC
Type 		F		F		F		F		F		F		F
```

### VARIABLE-DESCRIPTION

SECID 	Section ID. SECID is referenced on the *PART card and must be unique.

ELFORM 	Element formulation options, (see remark 3 below):
			EQ.0: 1 point corotational for *MAT_MODIFIED_HONEYCOMB.
				  See remark 4 below.
			EQ.1: constant stress solid element (default),
			EQ.2: fully integrated S/R solid. See remark 5 below,
			EQ.3: fully integrated quadratic 8 node element with nodal rotations,
			EQ.4: S/R quadratic tetrahedron element with nodal rotations,
			EQ.5: 1 point ALE,
			EQ.6: 1 point Eulerian,
			EQ.7: 1 point Eulerian ambient,
			EQ.8: acoustic,
			EQ.9: 1 point corotational for *MAT_MODIFIED_HONEYCOMB.
			 See remark 4 below.
			EQ.10: 1 point tetrahedron.
			EQ.11: 1 point ALE multi-material element
			EQ.12: 1 point integration with single material and void.
			EQ.13: 1 point nodal pressure tetrahedron for bulk forming.
			EQ.14: 8 point acoustic
			EQ.15: 2 point pentahedron element.
			EQ.18: 8 point enhanced strain solid element for linear statics only,
			EQ.31: 1 point Eulerian Navier-Stokes
			EQ.32: 8 point Eulerian Navier-Stokes
			
AET 	Ambient Element type: Can be defined for ELFORM 7, 11 and 12.
			EQ.1: temperature (not currently available),
			EQ.2: pressure and temperature (not currently available),
			EQ.3: pressure outflow,
			EQ.4: pressure inflow.(Default for ELFORM 7)
			
AFAC 	Smoothing weight factor - Simple average:
			EQ.-1: turn smoothing off.

BFAC 	Smoothing weight factor - Volume weighting

CFAC 	Smoothing weight factor - Isoparametric

DFAC 	Smoothing weight factor - Equipotential

START 	Start time for smoothing

END 	End time for smoothing

AAFAC 	ALE advection factor

### Remarks:

1. Element formulations 31 and 32 are used exclusively with the CFD option which requires
	ISOLTYP=4 on the *CONTROL_SOLUTION card. In this case, ELFORM=31 is used with
	INSOL=1 and ELFORM=32 is used with INSOL=3 on the *CONTROL_CFD_GENERAL
	card. Note that selection of the element formulation is automatic based on the value of INSOL
	for the CFD solver.
	
2. The keyword *CONTROL_SOLID activates automatic sorting of tetrahedron and pentahedron
	elements into type 10 and 15 element formulation, respectively. These latter elements are far
	more stable than the degenerate solid element. The sorting in performed internally and is
	transparent to the user.
	
3. For implicit calculations the following element choices are implemented:
		EQ.1: constant stress solid element,
		EQ.2: fully integrated S/R solid. See remark 5 below,
		EQ.10: 1 point tetrahedron.
		EQ.15: 2 point pentahedron element.
		EQ.18: 8 point enhanced strain solid element for linear statics only,
		EQ.31: 1 point Eulerian Navier-Stokes
		EQ.32: 8 point Eulerian Navier-Stokes
   If another element formulation is requested, LS-DYNA will substitute, when possible, one of
	the above in place of the one chosen.
	
4. Element formulations 0 and 9, applicable only to *MAT_MODIFIED_HONEYCOMB, behave
	essentially as nonlinear springs so as to permit severe distortions sometimes seen in honeycomb
	materials. In formulation 0, the local coordinate system follows the element rotation whereas in
	formulation 9, the local coordinate system is based on axes passing through the centroids of the
	element faces. Formulation 0 is preferred for severe shear deformation where the barrier is
	fixed in space. If the barrier is attached to a moving body, which can rotate, then formulation 9
	is usually preferred.
	
5. The selective reduced integrated solid element, element type 2, assumes that pressure is
	constant throughout the element to avoid pressure locking during nearly incompressible flow.
	However, if the element aspect ratios are poor, shear locking will lead to an excessively stiff
	response. A better choice, given poor aspect ratios, is the one point solid element which work
	well for implicit and explicit calculations. For linear statics, the type 18 enhanced strain element
	works well with poor aspect ratios. Please note that highly distorted elements should always
	be avoided since excessive stiffness will still be observed even in the enhanced strain strain
	formulations.