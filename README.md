# Cyber-Grid Architecture Modeling Language for Power Systems Documentation

**CyberGridML** aims to provide a modeling language and associated tooling targeting cyber-physical power grid systems, using **SysML v2**, **CyberGridML concepts**, and web-based engineering tools. 

CyberGridML provides modeling capabilities for representing the interaction between electrical grid assets, control functions, software resources, communication media, and computing infrastructure. The goal is to support clearer system architecture descriptions for modern power grids where cyber and physical components are increasingly interdependent.

## CyberGridML concepts 

CyberGridML is intended to foster Model-Based System Engineering for TSOs and DSOs, or any stakeholder interested in the field of power grid control. We provide for newcomers to this field of power grids a brief overview of the [power grid functions](./Principles/power-grid-functions.md) and the [main concepts](./Principles/concepts.md) handled in this project. 

CyberGridML is built upon a domain-specific modeling language for cyber-physical grid engineering.
The Cybergrid DSML has three modeling levels : 
*	Functional level (application), allowing to model a control principle.
*	Communication level, allowing to model telecommunication platforms (networks and communication infrastructure where the controllers are connected).
*	Execution level, allowing to model execution platforms (computing resources executing the control algorithms). 

[-> Go to modeling language description](./Principles/metamodels.md)

## User Documentation

CyberGridML is intended to be used according to a precise [workflow](./User-doc/modeling-workflow.md) which is designed to help the user model accurately the situation they want to represent. This theoretical workflow is implemented through a web-based user interface whose steps are documented in [Modeling guidelines](./User-doc/modeling-guidelines.md).

Furthermore, [Example models](./User-doc/example-models.md) are provided to help new users.

## Developer Documentation

Developers can find useful resources here :
* [Setup instructions](./Developer-doc/setup-instructions.md)
* [Architecture notes](./Developer-doc/architecture-notes.md)
* [CyberGridML profile documentation](./Developer-doc/CyberGridML-profile-documentation.md)
* [CyberGridML customization guide](./Developer-doc/Cybergrid_modeler_customization_guide.md)
* [Release and deployment instructions](./Developer-doc/release-and-deployment-instructions.md)



