## modified code : utils.py for pydmd package with randomized_svd

**[Optional]**: if you want to increase the computational efficiency for DMD, use randomized_svd from sklearn.utils.extmath.
1. find .../pyDMD/pydmd/utils.py
2. import randomized_svd  
from sklearn.utils.extmath import randomized_svd  
3. replace np.linalg.svd with randomized_svd in compute_svd:
#U, s, V = np.linalg.svd(X, full_matrices=False) # at line around 184
U, s, V = randomized_svd(X, n_components=svd_rank,random_state=42)  
4. then install pydmd again with modified source code
5. you can also use the utils.py in folder .../code_utils/utils.py to replace the .../pyDMD/pydmd/utils.py


