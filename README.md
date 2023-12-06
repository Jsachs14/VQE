# VQE
A repository that contains test python files for Variational Quantum Eigensolver on basic Hamiltonian systems. 

This repository was created by Jonah Sachs in conjunction with projects and personal research for a graduate course in Quantum Computing at Washington University in St. Louis.

Future work will include a latex doc detailing the steps and basics behind VQE.


VQE_1.ipynb:
This is a 4 qubit example currently using the toy Hamiltonian (Z ^ Z) ^(I^2). The Hamiltonian could be changed to experiment with other 4 qubit systems. The ansatz for this example is implemented using the EfficientSU2 gate from qiskit.circuit.library. The gate has 4 * num_qubit parameters. The gate has been included for reference for 4 qubits in Efficient_SU2.png. Optimization is done using SPSA, and QasmSimulatorPy was used for quantum simulation. The results are plotted in the end using matplotlib compared to the target ground state eigenvalue. Iterations over runtime were also plotted to determine efficiency over time during the VQE process.



VQE_2.ipynb:
This is a 1 qubit example that randomly generates (2x2) matrices until a matrix with real eigenvalues is produced. The initial ansatz is randomly generated, and EfficientSU2 is once again used as the ansatz gate. Simulations were again done using QasmSimulatorPy. Immediately apparent were results appearing below the ground state energy, which should not be possible due to the variational principle of QM. Other experiments with VQE point to the classical optimizer and processes as the explanation for these results. Testing was done with different optimizers to see the varying effects, but further studies will be done to truly understand this effect and its relevancy to VQE. Included in this folder are 4 pngs in the Optimizer subfolder. They are various runs using the same parameters, except for different optimizers. The same max_iterations was provided, but some optimizers halted before the value could be reached, causing differences in resolution. The optimizers used were ADAM, COBYLA, SLSQP, and SPSA. The difference in ground state energy is due to the randomization of the Hamiltonian, but otherwise, runs were identical.



VQE_3.ipynb: 
A more chemistry based example. This file attempts to model the ground state energy of LiH using VQE. The majority of methods were sourced from qiskit.aqua and qiskit.chemistry. The function iterates over different radial distances between the Li and H atoms. A range of [.5,4.25] Angstrom was used with an initial guess of .725 Angstrom. PySCF driver was used to create a basis set of functions that are used to describe the spread of the electrons in the molecule (combined atomic orbitals to approximate molecular orbital). The Hamiltonian class from qiskit.chemistry was used to formulate the Hamiltonian. NumpyMinimumEigensolver was used to exactly solve for the eigenvalues, saving them to compare to the VQE result. SLSQP with 1000 max_iterations was used as the optimizer, and UCCSD was used for the ansatz. The statevector simulator was used for quantum simulation. The exact result from Numpy, the Hartree-Fock approximation energy sourced from the VQE algorithm, and the VQE results were all plotted using matplotlib. The error difference between VQE and the exact energies was also shown using a scatter plot.



VQE_4.ipynb:
A VQE method built without qiskit's VQE methods. Uses numpy, cmath, random, math to build Hamiltonian and Qubit classes. scipy.optimizer was used for optimization, with method = 'Powell' and a randomly selected initial point as the ansatz. Due to the lack of proper ansatz, the results of this are interesting. Clear spikes can be observed which are not present in the other VQE files. These can be reduced at different iterations.  


If you're running into any errors I've included a requirements.txt file which contains all the packages I used to run these files. There are clear deprecation issues involving examples with VQE due to changes in IBM's qiskit.aqua library. Keep in mind that this is my environment for all QC applications I've done, and not all libraries will be neccessary for VQE. You can install them using pip with the command `pip install -r requirements.txt`, or just parse through if you're running into errors. If you're still having issues, feel free to reach out. My email is:
j.sachs@wustl.edu





