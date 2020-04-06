In this section, the element formulation, integration rule, nodal thicknesses, and cross
sectional properties are defined. All section identifiers (SECID’s) defined in this section must be
unique, i.e., if a number is used as a section ID for a beam element then this number cannot be used
again as a section ID for a solid element. The keyword cards in this section are defined in
alphabetical order:

*SECTION_BEAM
*SECTION_DISCRETE
*SECTION_SEATBELT
*SECTION_SHELL_{OPTION}
*SECTION_SOLID_{OPTION}
*SECTION_SPH
*SECTION_TSHELL

The location and order of these cards in the input file are arbitrary.
An additional option _TITLE may be appended to all the *SECTION keywords. If this option is
used then an addition line is read for each section in 80a format which can be used to describe the
section. At present LS-DYNA does make use of the title. Inclusion of titles gives greater clarity to
input decks.