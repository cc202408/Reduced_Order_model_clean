# ME5311 project

## Installation

> Clone project
```
git clone https://github.com/cc202408/Reduced_Order_model_clean.git
cd Reduced_Order_model_clean
```

> Create virtual environment
```
virtualenv myvenv
source myvenv/bin/activate
```
> Install all requirements
```
#install intel numpy to increase computational efficiency
pip install -i https://pypi.anaconda.org/intel/simple numpy  
#other requirements
pip3 install -r requirements.txt
```

> Install Jupyter notebook kernel
```
python -m ipykernel install --user --name myvenv --display-name "Python (myvenv)"
```

## Data
Data should be put under .../project_Data/t2m.nc

## For DMD
> Install pyDMD from source code
```
# git init
git submodule add https://github.com/mathLab/PyDMD.git pyDMD
cd pyDMD
pip install -e .
```

## run DMD
T2M data: project_DMD_t2m.ipynb
SLP data: project_DMD_slp.ipynb

**[Optional]**: if you want to increase the computational efficiency for DMD, use randomized_svd from sklearn.utils.extmath.
1. find .../pyDMD/pydmd/utils.py
2. import randomized_svd  
from sklearn.utils.extmath import randomized_svd  
3. replace np.linalg.svd with randomized_svd in compute_svd:
#U, s, V = np.linalg.svd(X, full_matrices=False) # at line around 184
U, s, V = randomized_svd(X, n_components=svd_rank,random_state=42)  
4. then install pydmd again with modified source code
5. you can also use the utils.py in folder .../code_utils/utils.py to replace the .../pyDMD/pydmd/utils.py

## For SINDy-SHRED
> clone the source code
```
git submodule add https://github.com/gaoliyao/sindy-shred.git SINDy_SHRED
```

## run SINDy-SHRED
T2M data: project_SINDy_SHRED_t2m.ipynb
SLP data: project_SINDy_SHRED_slp.ipynb

## acknowlege: https://github.com/gaoliyao/sindy-shred
