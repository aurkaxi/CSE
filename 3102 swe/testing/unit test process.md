because a component is not a standalone program, a driver and/or a stub is developed for each unit test. the environment is shown in figure 3 below
![[unit test process.png]]

driver is usually a main program that accepts test case data, passes such data to the components to be tested and prints relevant results.

stub serves to replace modules that are subordinate (call by) to the module to be tested. a stub or dummy subprogram uses the subordinate module's interface, may do minimal data manipulation, prints verification of entry and return controls to the module undergoing testing.