# Quantum Coalition Hackathon 2022 Amazon Braket Challenge Submission 

## Implementation of the Quantum Restricted Boltzmann Machine Neural Network Algorithm using Variational Methods

### Background of the Restricted Boltzmann Machine 

The RBM is a type of Boltzmann machine with two layers of binary-valued units and 2 hidden layers with no intra-layers connection. By introducing the restrictions of limited laayers we make the hidden units become conditionally independent given the states of the visible units giving a faster convergance time and evaluation of data. 

An example of the RBM in our case:

![Screen Shot 2022-04-10 at 5 32 39 AM](https://user-images.githubusercontent.com/30132476/162618297-e5254fb6-8858-4bdc-87fa-c51878f326db.png)

By using the QRBM we are first initializing the network parameters such as weights and biases randomly and then providing epoch parameters and perform a grid search for random weights to find out better loss. The variational aspects for the quantum algorithm comes in computing the expectation values thus making this a variational hybrid algorithm. 


## Problem Description

The problem of approimating the statistics of a thermal state of a given hamiltonian is a largely and expensive computational problem in Statritcal Physics. 

For a given Ising hamiltonian: ![Screen Shot 2022-04-10 at 4 42 58 AM](https://user-images.githubusercontent.com/30132476/162616395-72185b4f-a1fd-46e5-8665-36631eb8302f.png) ![Screen Shot 2022-04-10 at 4 43 42 AM](https://user-images.githubusercontent.com/30132476/162616421-c2e74594-56b1-4b90-ba1f-bb71995cb223.png)

For a given thermal state: ![Screen Shot 2022-04-10 at 4 46 07 AM](https://user-images.githubusercontent.com/30132476/162616505-2de4c95a-470a-4838-9a50-1808f26d53df.png) for the above ising hamiltonian we have to find a set of states ![Screen Shot 2022-04-10 at 4 44 20 AM](https://user-images.githubusercontent.com/30132476/162616445-5ad822c8-da39-4bbe-9da7-b015d45a0df9.png) where ![Screen Shot 2022-04-10 at 4 44 46 AM](https://user-images.githubusercontent.com/30132476/162616459-8200105b-39ee-4509-b9d4-d2270183a846.png) is a set of variational parameters for the state preparation ansatz that we must find and optimize using the QRBM Algorithm.

We have to find the variational parameters using the QRBM Algorithm and compare its speed over a classical Restricted Boltzmann Machine Algorithm for complicated Hamiltonians.





## Results

By using our Quantum circuit for the algorithm to be: 

![Screen Shot 2022-04-10 at 5 06 51 AM](https://user-images.githubusercontent.com/30132476/162617273-8a303b26-cbc4-45da-9c29-3a9dea7c8aa7.png)


Upon training and getting the measurements we get:

![Screen Shot 2022-04-10 at 5 18 05 AM](https://user-images.githubusercontent.com/30132476/162617700-bfa87583-d91b-4f92-8f6f-722a45e3d9a7.png)


And the correct values computed for the hamiltonian thermal states are:

![Screen Shot 2022-04-10 at 5 25 12 AM](https://user-images.githubusercontent.com/30132476/162618000-27f60b50-72e2-45c0-80bf-38b40c2eec93.png)


Based on this we see a percente difference of about 1% in the calculations and this calculation was done with 1000 epochs.






## Instructions on Running the Project

Step 1: Clone the Project Repository into AWS Braket or your local machine.

Step 2: Make sure the following packages or softwares are installed:
        - Python Packages (pip install {package name}: pyquil, scipy, funcsigs, numpy, functools, typing, collections
        - If running on Braket make sure it is running on the Aspen-11 Rigetti Device
        - If running on local machine make sure the Rigetti Forest SDK is installed https://pyquil-docs.rigetti.com/en/1.9/start.html#
            - Go to terminal and run "qvm -S" and "quilc -S" to start the Quantum virtucal machine and the quil compiler from rigetti 
        - Make sure python, conda or jupyter notebook are installed if running on a local machine
        
Step 3: Run the jupyter notebook QBM.ipynb. Keep in mind the epochs and initial data can be adjusted in the notebook itself but keep in mind the entire algorithm 
        takes 30 minutes for 100 epochs for the given hamiltonian.






## Side Comments on the project

Due to the lack of time could not compute several epoch runs therefore no graph available to show accuracy vs number of epochs however the above result is with the 1000 epochs.

The VQE and the QAOA algorithms are copied from a library called grove and the code after VQE and QAOA are code written for this project and the implementation of QRBM.
