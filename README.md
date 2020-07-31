# km_unit: Unit Testing For Kinetics Models In Systems Biology


Over the last decade, kinetics models in systems biology have grown in size from small tens of reactions to hundreds. Constraint based models are larger still, often many thousands of reactions. This increasing complexity raises concerns about the accuracy and limitations of quantitative models in systems biology.

Testing is commonly used to detect errors. Testing can be of two types. Validation testing seeks to assess the accuracy and utility of the models. For example, does the model accurately predict values of new experimental results? Does the model provide helpful insights, such as disease targets? Validation tests are constructed in a manner that is specific to the model and how it will be used.

A second kind of testing is verification. Verification checks if there are errors in the model implementation or the way in which the model is executed. To illustrate, consider the following incorrect implementation of a kinetics model of a two species linear pathway with mass action kinetics:

- ``R1: S1 -> S2; k1*S1``
- ``R2: S2 -> S3; k2*S1``

The network is expressed in the human readable Antimony language in which the label before the colon identifies the reaction, and the kinetics expression follows the semi-colon. We see that there is a typographical error in the kinetics expression for R2 in that S1 appears instead of S2. This incorrectly implemented reaction network is still a linear pathway, but it does not have the desired kinetics. As model complexity grows, it will become increasingly common to introduce such errors and increasingly difficult to discover them. For example, Neupane et al. report errors in codes that calculate NMR shifts as a result  of differences between operating systems on which the scripts are run. “This simple glitch in the original script calls into question the conclusions of a significant number of papers on a wide range of topics”.

In software systems, verification is done using unit tests. Unit tests are codes written to verify the implementation of individual functions. For example, consider a unit test for the function ``findPrimes`` that finds the first *N* prime numbers, where *N* is an argument to the function. A unit test for ``findPrimes`` might check that if *N* is larger than 2, then 2 is included in the result of the function. This unit test does not prove that ``findPrimes`` is implented correctly, and it does not validate that ``findPrimes`` is what should be implemented. But the unit test does verify one expected behavior of ``findPrimes``.

This project is about developing unit test capabilities for kinetics models in systems biology. A unit test may focus on a single sub-model, a chemical pathway, or even an individual chemical species. To illustrate, consider a linear pathway (e.g., the first part of glycolysis considered in isolation). One expectation of such a pathway is that *A(n,t)*, the amount of species *n* at time *t*, is equal to *A(n, 0) + R(n-1, n, t) – R(n, n+1, t)*, where *R(n, n+1, t)* is the number of reactions that occur for times in [0, 1]. Note that since we are evaluating the results of a simulation, we have access to all data necessary to test if this equality holds.
The project goals for km_unit are:

1.	Create a software infrastructure for testing kinetics models similar to the python package unittest. The infrastructure should support models in the SBML format.
2.	Create support utilities that extract characteristics of time series that are useful for testing dynamics. Examples are: cumulative amount of a chemical species and number of reactions. The approaches should apply to both deterministic and stochastic simulations.
3.	Develop tests for the dynamics of common structures in biochemical networks such as: linear pathways, branched pathways, and feedback.
4.	Develop a tool that automatically generates tests for an existing model as a way to automate the construction of "regression tests".
5.	Validate the approaches using examples from BioModels.


