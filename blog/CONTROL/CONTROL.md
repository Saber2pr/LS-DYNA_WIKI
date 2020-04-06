The keyword control cards are optional and can be used to change defaults, activate solution
options such as mass scaling, adaptive remeshing, and an implicit solution; however, it is advisable
to define the *CONTROL_TERMINATION card. The ordering of the control cards in the
input file is arbitrary. To avoid ambiguities, define no more than one control card
of each type. The following control cards are organized in an alphabetical order:
	*CONTROL_ACCURACY
	*CONTROL_ADAPSTEP
	*CONTROL_ADAPTIVE
	*CONTROL_ALE
	*CONTROL_BULK_VISCOSITY
	*CONTROL_CFD_AUTO
	*CONTROL_CFD_GENERAL
	*CONTROL_CFD_MOMENTUM
	*CONTROL_CFD_PRESSURE
	*CONTROL_CFD_TRANSPORT
	*CONTROL_CFD_TURBULENCE
	*CONTROL_COARSEN
	*CONTROL_CONTACT
	*CONTROL_COUPLING
	*CONTROL_CPU
	*CONTROL_DYNAMIC_RELAXATION
	*CONTROL_ENERGY
	*CONTROL_EXPLOSIVE_SHADOW
	*CONTROL_HOURGLASS_{OPTION}
	*CONTROL_IMPLICIT_AUTO
	*CONTROL_IMPLICIT_DYNAMICS
	*CONTROL_IMPLICIT_EIGENVALUE
	*CONTROL_IMPLICIT_GENERAL
	*CONTROL_IMPLICIT_SOLUTION
	*CONTROL_IMPLICIT_SOLVER
	*CONTROL_IMPLICIT_STABILIZATION
	*CONTROL_OUTPUT
	*CONTROL_PARALLEL
	*CONTROL_RIGID
	*CONTROL_SHELL
	*CONTROL_SOLID
	*CONTROL_SOLUTION
	*CONTROL_SPH
	*CONTROL_STRUCTURED_{OPTION}
	*CONTROL_SUBCYCLE
	*CONTROL_TERMINATION
	*CONTROL_THERMAL_NONLINEAR
	*CONTROL_THERMAL_SOLVER
	*CONTROL_THERMAL_TIMESTEP
	*CONTROL_TIMESTEP
	
LS-DYNA’s implicit mode may be activated in two ways. Using the
*CONTROL_IMPLICIT_GENERAL keyword, a simulation may be flagged to run entirely in
implicit mode. Alternatively, an explicit simulation may be seamlessly switched into implicit mode at
a specific time using the *INTERFACE_SPRINGBACK_SEAMLESS keyword. The seamless
switching feature is intended to simplify metal forming springback calculations, where the forming
phase can be run in explicit mode, followed immediately by an implicit static springback simulation.
In case of difficulty, restart capability is supported. Seven keywords are available to support implicit
analysis. Default values are carefully selected to minimize input necessary for most simulations.
These are summarized below:

	*CONTROL_IMPLICIT_GENERAL
	Activates implicit mode, selects time step size.
	*CONTROL_IMPLICIT_SOLVER
	Selects parameters for solving system of linear equations [K]{x}={f}.
	*CONTROL_IMPLICIT_SOLUTION
	Selects linear or nonlinear solution method, convergence tolerances.
	*CONTROL_IMPLICIT_AUTO
	Activates automatic time step control.
	*CONTROL_IMPLICIT_DYNAMICS
	Activates and controls dynamic implicit solution using Newmark method.
	*CONTROL_IMPLICIT_EIGENVALUE
	Activates and controls eigenvalue analysis.
	*CONTROL_IMPLICIT_STABILIZATION
	Activates and controls artificial stabilization for multi-step springback.
	
