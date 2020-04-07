The keyword *SET provides a convenient way of defining groups of nodes, parts, elements,
and segments. The sets can be used in the definitions of contact interfaces, loading conditions,
boundary condtions, and other inputs. Each set type must have a unique numeric identification. The
keyword control cards in this section are defined in alphabetical order:

	*SET_BEAM_OPTION
	*SET_DISCRETE_{OPTION}
	*SET_NODE_OPTION
	*SET_PART_OPTION
	*SET_SEGMENT_{OPTION}
	*SET_SHELL_OPTION
	*SET_SOLID_{OPTION}
	*SET_TSHELL_{OPTION}
	
An additional option _TITLE may be appended to all the *SET keywords. If this option is
used then an addition line is read for each section in 80a format which can be used to describe the set.
At present LS-DYNA does make use of the title. Inclusion of titles gives greater clarity to input
decks.

The GENERAL option is available for set definitions. In this option, the commands are
executed in the order defined. For example, the delete option cannot delete a node or element unless
the node or element was previously added via a command such as BOX or ALL.