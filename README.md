# ------ 2.2 Tester Programme ---------

# importing needed libraries, as well as functions from vector.py
import random
import vector

from vector import find_magnitude, sum_vectors, cross_product, dot_product, check_same, mult_scalar

# create function that creates random 3d vector using the random library

def create_rand_vect():
    vector = [float(random.randint(0,9)),float(random.randint(0,9)),float(random.randint(0,9))]
    return vector

# randomly create vectors v1, v2 and v3, storing as python lists

v1 = create_rand_vect()
v2 = create_rand_vect()
v3 = create_rand_vect()

# create function that checks identity v1 x v2 = −v2 x v1

def check_anti_commutative(vector1,vector2):
    LHS = cross_product(vector1,vector2) # gives left hand side
    RHS = mult_scalar((-1),(cross_product(vector2,vector1))) # gives right hand side
    if check_same(LHS,RHS) == True: # hence checks both sides of the equation equal
        return True
    else:
        return False

# create function that checks v1 × (v2 + v3) = (v1 × v2) + (v1 × v3)

def check_distributive(vector1,vector2,vector3):
    LHS = cross_product(vector1,(sum_vectors(vector2,vector3))) # gives left hand side
    RHS = sum_vectors(cross_product(vector1,vector2), cross_product(vector1,vector3)) # gives right hand side
    if check_same(LHS,RHS) == True: # hence checks both sides of the equation equal
        return True
    else:
        return False

# create function that checks v1 × (v2 × v3) = (v1 · v3)v2 − (v1 · v2)v3

def check_vector_triple_product(vector1,vector2,vector3):
    LHS = cross_product(vector1, (cross_product(vector2,vector3))) # gives left hand side
    RHS_first_term = mult_scalar((dot_product(vector1,vector3)),vector2) # gives (v1 · v3)v2
    RHS_second_term = mult_scalar((-1)*(dot_product(vector1,vector2)),vector3) # gives − (v1 · v2)v3
    RHS = sum_vectors(RHS_first_term,RHS_second_term) # gives right hand side
    if check_same(LHS,RHS) == True: # hence checks both sides of the equation equal
        return True
    else:
        return False

def main():

    #printing the vectors and their magnitudes :

    print("v1 = " + str(v1) + ", and is of magnitude " + str(find_magnitude(v1)))
    print("v2 = " + str(v2) + ", and is of magnitude " + str(find_magnitude(v2)))
    print("v3 = " + str(v3) + ", and is of magnitude " + str(find_magnitude(v3)))

    # printing the sum, dot product and cross product of v1 and v2

    print("The vector sum of v1 and v2 is " + str(sum_vectors(v1,v2)))
    print("The dot product of v1 and v2 is " + str(dot_product(v1,v2)))
    print("The cross product v1 x v2 is " + str(cross_product(v1,v2)))

    # printing the results of these checks because why not 

    print("Using Vectors v1,v2 and v3, the following vector identities are shown to be (hopefully) True:")
    print("v1 × v2 = −v2 × v1 : " + str(check_anti_commutative(v1,v2)))
    print("v1 × (v2 + v3) = (v1 × v2) + (v1 × v3) : " + str(check_distributive(v1,v2,v3)))
    print("v1 × (v2 × v3) = (v1 · v3)v2 − (v1 · v2)v3 : " + str(check_vector_triple_product(v1,v2,v3)))

main()
