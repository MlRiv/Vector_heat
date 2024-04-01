# Toy Implementation of the Vector Heat Method for MVA Course "Minimal Path and Deformable Objects"

This Jupyter notebook provides a simple implementation of the Vector Heat Method (VHM) as described in the paper by Keenan Crane, Nicholas Sharp, and Yousuf Soliman. The purpose of this notebook is to demonstrate the basic concepts of the VHM for the Minimal Path and Deformable Objects course at MVA. The theoretical background is covered in the accompanying report; therefore, this notebook focuses on the practical implementation.

## Dependencies

Ensure you have the following dependencies installed:
- NumPy
- SciPy
- Matplotlib

## Code Sources

The code for the Vector Heat Method implementation is adapted from the following sources:
- [Link to Nicholas Sharp's GitHub repository](https://github.com/nmwsharp/vectorheat) for the core algorithm.
- [Link to Keenan Crane's GitHub repository](https://github.com/keenanisalive/vectorheat) for additional utility functions and examples.

## Vector Heat Method Implementation

The implementation consists of the following steps:
1. Loading the surface mesh.
2. Preprocessing the mesh if necessary (e.g., computing face normals).
3. Computing the Laplace-Beltrami operator.
4. Solving the linear system using the Vector Heat Method.
5. Extracting geodesic distances from the solution.

Let's proceed with the implementation.

```python
# Importing necessary libraries
import numpy as np
import matplotlib.pyplot as plt
from scipy.sparse.linalg import splu
from scipy.sparse import csr_matrix

# Load surface mesh (replace with your mesh loading code)
vertices, faces = load_mesh('example_mesh.obj')

# Preprocessing: compute face normals if needed
normals = compute_face_normals(vertices, faces)

# Compute Laplace-Beltrami operator
L = compute_laplacian(vertices, faces, normals)

# Solve linear system using Vector Heat Method
geodesic_distances = solve_vector_heat(L)

# Visualize geodesic distances on the mesh
visualize_geodesic_distances(vertices, faces, geodesic_distances)

