# Faddeeva

This project contains Matlab code for evaluation of the Faddeeva function w(z), for complex z, where

w(z) := exp(-z^2) erfc(-i z),

where erfc is the standard complementary error function and i = sqrt(-1). The methods used are based on representations for w(z) as an integral on the real line [1, (3)], and the evaluation of these integrals by modified trapezoidal rules. See [1] and its Supplementary Materials for more details.

The Matlab codes in this project are:

wTrap.m         Matlab function, with inputs z and N, that evaluates w(z) using N+1 quadrature points in the case when z=x+iy with x,y >= 0. 
                (N = 11 is recommended to achieve absolute and relative errors no larger than 2e-15.) 
                
wTrapWCP.m      Matlab function, with inputs z and N, that evaluates w(z) using N+1 quadrature points for arbitrary complex z, by calling wTrap and using symmetries of w(z).
                (Again, N = 11 is recommended.)
                
test_wTrapWCP.m Matlab script file to run to test wTrapWCP (and wTrap which it calls).
            

Mohammad Al Azah (Al Hussein Technical University, Amman, Jordan) and
Simon Chandler-Wilde (University of Reading, UK)

[1] M. Al Azah and S. N. Chandler-Wilde, Computation of the complex error function using modified trapezoidal rules, 2020, arXiv:2010.05659
