# Algorithm for QR Decomposition
## Aim:
To implement QR decomposition algorithm using the Gram-Schmidt method.
## Equipment’s required:
1.	Hardware – PCs
2.	Anaconda – Python 3.7 Installation / Moodle-Code Runner
## Algorithm:
1.	Intialize the matrix Q and u
2.	The vector u and e is given by

    ![eqn1](./ex4.jpg)

    ![eqn2](./ex6.jpg)

    ![eqn3](./ex3.jpg)

3.	Obtain the Q matrix   
    ![eqn4](./ex1.jpg)
4.	Construct the upper triangular matrix R
    ![eqn5](./ex2.jpg)



## Program:
### Gram-Schmidt Method

<img width="762" height="360" alt="image" src="https://github.com/user-attachments/assets/2528b6d4-1852-4d62-9550-6a9dbb3b4d05" />

```
''' 
Program to QR decomposition using the Gram-Schmidt method
Developed by: Mohamed Asad S
RegisterNumber: 212225040238
'''

import os
os.environ["OPENBLAS_NUM_THREADS"]="1"
import numpy as np
def qr_decomposition(A):
    A = np.array(A, dtype=float)
    m, n = A.shape
    Q = np.zeros((m, n))
    R = np.zeros((n, n))
    for j in range(n):
        v = A[:, j]
        for i in range(j):
            R[i, j] = np.dot(Q[:, i], A[:, j])
            v = v - R[i, j] * Q[:, i]
        R[j, j] = np.linalg.norm(v)
        Q[:, j] = v / R[j, j]
    return Q, R
A = np.array(eval(input()))
Q, R= qr_decomposition(A)
print("The Q Matrix is\n", Q)
print("The R Matrix is\n", R)
```

## Output

<img width="1192" height="487" alt="image" src="https://github.com/user-attachments/assets/22731748-1833-4da7-838b-453a70b4a57c" />


## Result
Thus the QR decomposition algorithm using the Gram-Schmidt process is written and verified the result.
