is a systematic technique for constructing a programs structure while at the same time conducting tests to uncover errors associated with interfacing.
the objective is to take unit tested components and build a program structure that has been dictated by design.

types of approach:
1. non incremental / big bang approach: all components are combined in advance
2. incremental approach: the program is constructed and tested an small increments, where errors are easier to isolate and correct, interfaces are tested completely and systematic testing is applied. types of incremental integration
	1. top down integration
	2. bottom up integration

top down integration
1. incremental approach to construct a program structure
2. modules have control hierarchy and subordinate to main module
3. apply breadth first or depth first manner. the modules in figure can be tested in five steps
	1. the main control module is used as a test driver and stubs are substituted for all components directly sub-ordinate to main control module.
	2. Depending on the integration approach (BF or DF), subordinate stubs are replaced one at a time.
	3. Test is conducted as each component is integrated.
	4. On completion of each set of tests, another stub is replaced with the real component.
	5. Regression testing may be conducted to ensure that new errors have not been introduced.
![[Pasted image 20261112085122.png]]

bottom up integration 
begins construct and testing atomic modules, so modules integrated from the bottom up, processing required for a component subordinate to a given level is always available and stub is not needed.
steps:
1. Low level components are combined as clusters/builds that perform a specific SW sub-function.
2. A driver is written to coordinate test case input output.
3. The cluster is tested.
4. Drivers are removed and clusters are combined upward in the program structure.
![[Pasted image 20261112085239.png]]