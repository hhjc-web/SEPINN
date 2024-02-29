Singularity-enriched physics-informed neural network(SEPINN)

These examples are for the article "Solving Possion problems in polygonal domains with singularity enriched physics neural network".

Environment requirements:

1. Set up Anaconda at: https://www.anaconda.com/
2. Build Python environment
3. Creating a Virtual Environment by running 
conda create -n env_name python=3.10 (python version)
4. Download environment.txt and running
pip install -r environment.txt
to the environment you create.

Then you may run the programme on Jupyter notebook.

Comments for the code:

SEPINN for 2-d problem: (Example 1 and Exmaple 2)

1. Data Prep
In this part we create the domain, either L-shaped or rectangle domain.

2. Test Data
The teat data is chosen in this part in X_v_test, and the true solution for the regular part is v_true and whole part is u_true. If you were to test the code with other functions, just change the function here.

3. Training Data
In this part we construct the training data for boundary and domain. the data is uniformly distributed.

4. SEPINN
This part is the neural network model of the SEPINN.
_init_: some paramrters we use in the setting, and self.lambdah is the lambda we train
loss_BC, loss_PDE, loss: the loss function
test: to test the model

5. Loss Function
The main part of the model. In this part, we give the sampling points, the network structure, and put them into the model to train.

SEPINN for 3-d problem: (Example 3 and Exmaple 4) 

The 3-d problem is very similar to 2-d one, we only mention some model differences.
SEPINN-cutoff:  In _init_ function, the lambdah should be a vector with the length you want to cut off.
SEPINN-nn: In _init_ function, we use linears to represent the parameters of v and linears0 to represent the parameters of \PHi.

SEPINN for eigenvalue problem:

We use SEPINN to solve eigenvalue problem in L-shped doamin in Example 5, where you can find the formulation of loss function in our article. rayleigh1 and rayleigh2 are two rayleigh quotients for each eigenfunction. In our experiments we only use loss but not loss_new. loss_new function is contained in closure where we tested for L-BFGS optimizer.
