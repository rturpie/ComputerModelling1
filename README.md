# ComputerModelling1

# ----- 2.1 Vector Manipulation with Lists --------

v1 = [1,3,5] # test vector 1
v2 = [2,5] # test vector 2

# creating a function that can find the magnitude of a vector squared

def find_squared_magnitude(vector):
    """
    Finds the magnitude squared of a vector
    :param vector: vector represented as python list
    :return: magnitude of the vector squared 
    """
    squared_magnitude = 0
    for i in range(len(vector)):
        squared_magnitude += (vector[i])**2
    return squared_magnitude

# creating a function that will find the magnitude of a vector

def find_magnitude(vector):
    """
    Finds the magnitude of a vector
    :param vector: vector represented as python list
    :return: magnitude of the vector  
    """
    x = (find_squared_magnitude(vector))**0.5
    return x

# creating a function that will multiply a vector by scalar c

def mult_scalar(c,vector):
    """
    Multiplies a vector by a scalar
    :param c: scalar ??????
    :param vector: vector represented as python list
    :return: the vector found by multiplying the original vector by the scalar
    """
    new_vector = []
    for i in range(len(vector)):
        new_vector.append(c*(vector[i]))
    return new_vector

# creating a function that will divide a vector by scalar c

def div_scalar(c,vector):
    """
    Multiplies a vector by a scalar
    :param c: scalar ??????
    :param vector: vector represented as python list
    :return: the vector found by multiplying the original vector by the scalar
    """
    new_vector = []
    for i in range(len(vector)):
        new_vector.append((vector[i])/c)
    return new_vector

# creating a function that will find the vector sum of two vectors

def sum_vectors(vector1,vector2):
    new_vector = []
    if len(vector1) == len(vector2):
        for i in range(len(vector1)):
            new_vector.append(vector1[i] + vector2[i])
        return new_vector

# creating a function that will find the vector difference of two vectors

def diff_vectors(vector1,vector2):
    new_vector = []
    if len(vector1) == len(vector2):
        for i in range(len(vector1)):
            new_vector.append(vector1[i] - vector2[i])
        return new_vector

# creating a function that will find the cross product of two 3d vectors
# done using cross product expansion

def cross_product(v1,v2):
    c_p = [(v1[1]*v2[2] - v1[2]*v2[1]), (v1[2]*v2[0] - v1[0]*v2[2]), (v1[0]*v2[1] - v1[1]*v2[0])]
    return c_p

# creating a function that will find the dot product of two vectors

def dot_product(vector1,vector2):
    new_vector = 0
    if len(vector1) == len(vector2):
        for i in range(len(vector1)):
            new_vector += vector1[i]*vector2[i]
        return new_vector

# creating a function that will check if two vectors are the same

def check_same(vector1, vector2):
    if len(vector1) == len(vector2):
        so_far = True
        for i in range(len(vector1)):
            if vector1[i] != vector2[i]:
                so_far = False
        return so_far
    return False

v1 = [-1,2,3]
print(mult_scalar(3,v1))
