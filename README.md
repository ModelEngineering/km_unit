# km_unit: Unit Testing for Kinetics Models

The increasing complexity of kinetics models necessitates a more systematic approach to testing. 

Testing can be of two types.
Validation testing seeks to assess the accuracy and utility of the models. For example, does the model accurately predict values of new experimental results? Does the model provide helpful insights, such as disease targets? Validation testing is specific to the model and the model stakeholders.

A second kind of testing is verification.
Verification checks if the model implementation is consistent with its specification.
This is akin to unit tests in software systems.
Verification testing is rarely done for kinetics models.
For example, is there a typographical error in which the incorrect chemical species is specified a pathway reaction?

This project is about developing unit test capabilities for kinetics models in systems biology.
The project goals are:

1. Create a software infrastructure for testing kinetics models similar to the python package ``unittest``. The infrastructure should support models in the SBML format, antimony, and roadrunner.

1. Create support utilities that extract characteristics of timeseries that are useful for testing dynamics. Examples are: series min and max, time of the max, curve type (e.g., monotone increasing, monotone decreasing, concave).

1. Develop tests for the dynamics of common structures in biochemical networks such as: linear pathway, branched pathway, and feedback.

1. Develop a tool that automatically generates tests for an existing model as a way to automate the construction of "regression tests".

1. Validate the approaches using examples from [BioModels](https://www.ebi.ac.uk/biomodels/).
