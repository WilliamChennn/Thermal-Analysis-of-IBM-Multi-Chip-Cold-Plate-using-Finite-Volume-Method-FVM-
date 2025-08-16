# Thermal Analysis of IBM Multi-Chip Cold Plate using Finite Volume Method (FVM)
This project implements a 2D Finite Volume Method (FVM) to analyze conduction and convection heat transfer in a cold plate with 28 discrete points. FVM is a computational technique that decomposes a complex system into smaller control volumes (nodes), each governed by equations predicting its behavior. By assembling individual volume behaviors, FVM simulates the thermal response of the entire system under various physical conditions. This method is widely used in engineering and physics for its ability to accurately predict the response of structures and materials to forces, heat, and other external factors.

## Features 
### Industrial Applications
- Modular 2D FVM framework suitable for analyzing multi-chip cold plates and other thermal management systems.  
- Extensible to microelectronics cooling, semiconductor packaging, and complex conduction-convection scenarios.  
- Provides a lightweight simulation tool for rapid prototyping and design verification in engineering environments.

## Objective
The goal of this project is to create a general, reusable Python code for thermal analysis using a 2D Linked List to solve conduction and convection problems. Users can simply set node positions and conditions to solve similar heat transfer problems across different materials and boundary conditions, enabling a lightweight tool for engineering applications.

## Data Structure Choice: 2D Linked List
- **Why 2D Linked List**: The 2D Linked List intuitively represents the computational grid, simplifying coding and debugging by directly mapping physical geometry to the grid. Its dynamic nature allows flexible modification of the mesh, facilitating different material properties and boundary conditions.  
- **Node Structure**: Each node contains:
  - `number`: node ID
  - `up, down, left, right`: neighbor pointers
  - `is_convection`: True if the node has convection
  - `is_heat`: True if the node is a heat source
  - `is_virtual`: True for virtual nodes representing heat sources or convection
  - `is_fixed` and `fixed_temp`: fix temperature if needed
- **Grid Connectivity**: Neighbor connections handle normal, convection, heat source, and fixed temperature conditions, ensuring correct assembly of the FVM equations.

## FVM Implementation
- Nodes are stored in an array for efficient traversal.  
- Heat transfer coefficients are calculated using:
  - Fourier’s Law: `q_x = K * A * ΔT / ΔX`  
  - Newton’s Cooling Law: `q = K * A * (T_surface - T_fluid)`  
- Coefficients are assembled into matrices `A` and `C` to solve the linear system `A * T = C`, yielding the temperature distribution across the 2D domain.

## Challenges & Solutions
- **Challenge**: Handling non-rectangular grids with 2D Linked List is difficult due to its inherent rectangular structure.  
- **Solution**:  
  - Hybrid data structures combining Linked List, arrays, and tree structures for irregular shapes.  
  - Enhanced node class storing geometry information for accurate representation.  
  - Dynamic mesh refinement algorithms for local resolution adjustment.

## Advantages
- Easy to implement and lightweight, suitable for simple 2D problems without large software installation.  
- User-friendly interface with Python, enabling quick setup and execution.  
- Can be extended to larger-scale thermal simulations by increasing mesh density and defining boundary conditions.

## Limitations
- Current implementation only supports rectangular grids and lacks dynamic mesh refinement.  
- Not optimized for high-performance computing, but sufficient for educational and prototyping purposes.

## Summary
This project combines computer science and mechanical engineering knowledge to provide a simple, flexible, and reusable thermal analysis tool. While limited to rectangular grids, the approach demonstrates fundamental engineering problem-solving skills and lays the groundwork for future extensions to complex thermal simulations in industrial applications.
