## Power Grid Functions

CyberGridML provides a modeling language to reason about electrical grids, their control functions, and the infrastructure implementing those. 
This document provides an overview of power grid functions for non-specialists, and gives some insights as to what this project aims to do.

The electricity grid is essential for society, ensuring continuous access to electricity for everyone. On a continental scale, it is considered the most complex technological system ever created by mankind. The main role of an electrical grid is to deliver electricity from producers to consumers. As there are fewer production units than consumers, and as these production units can be far from the large consumption centers, the electrical grid has at the same time a function of transmission and distribution of the electrical energy.

The electrical grid has five main functions: 
*	**Generation**: producing electricity to provide a regular, stable, and secure supply service. This function applies to the big production sites, such as nuclear power plants, gaz power plants or hydroelectric dams. Distributed Energy Resources (DER) are small-scale energy systems that can also contribute to the generation function. 
*	**Transmission**: The high voltage transmission grid carries electricity from large production sites to the distribution grid, making electricity travel over long distances with as few losses as possible. In order to achieve this, voltage coming from the generation system and entering the transmission grid is very high and is carried through high voltage lines.
*	**Distribution**: The low voltage distribution grid delivers electricity to each end user (industries, households, etc.) from the “source” substations of the transmission grid. The voltage is stepped down between the transmission grid and the distribution grid, and then stepped down again within the distribution grid to reach the voltages intended for consumers.
*	**Protection**: the protection function ensures the safety of people and property during the transmission of electricity. 
*	**Consumption**: The consumption function uses electricity for various purposes.

Historically, these functions have been organized in a generally hierarchical, top-down manner, from production to consumption. This organization has been changing for some time now, as other functions have appeared, such as distributed energy resources (DER) or storage (batteries). In the context of the introduction of these new functions, new control functions may be necessary. CyberGridML allows to model various architectures for these control mechanisms in order to analyze them.



