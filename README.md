# Faddeeva

This project contains Matlab code for evaluation of the Faddeeva function w(z), for complex z, where

w(z) := exp(-z^2) erfc(-i z),

where erfc is the standard complementary error function and i = sqrt(-1). The methods used are based on representations for w(z) as an integral on the real line [1, (3)], and the evaluation of these integrals by modified trapezoidal rules. 

The specific approximation w_N(z) implemented is the approximation obtained when the modified trapezoidal rule is used with N+1 quadrature points. This new method is attractive becuase it is provably exponentially convergent at a rapid rate, the accuracy improving by a factor exp(pi) = 23.1... for each extra quadrature point. (The results in [1, Figure 2] demonstrate that this convergence is achieved in practice in double precision arithmetic.)

Precisely [1, Theorem 1.1] proves that |w(z)-w_N(z)| \leq 0.7 exp(-pi N) for all non-negative integers N and all complex z (in exact arithmetic), and a similar bound holds on the relative error in the upper complex half-plane where w(z) is non-zero.

See [1] and its Supplementary Materials [2] for more details.

The Matlab codes in this project are:

wTrap.m         Matlab function, with inputs z and N, that evaluates w_N(z) using N+1 quadrature points in the case when z=x+iy with x,y >= 0. 
                (N = 11 is recommended to achieve absolute and relative errors no larger than 1.4e-15) 
                
wTrapWCP.m      Matlab function, with inputs z and N, that evaluates w_N(z) using N+1 quadrature points for arbitrary complex z, by calling wTrap and using symmetries of w(z).
                (Again, N = 11 is recommended.)
                
test_wTrapWCP.m Matlab script file to run to test wTrapWCP (and wTrap which it calls).

The remaining Matlab codes in this project are the files: wTrap_Q.m, a quadruple precision version of wTrap.m (which implements quadruple precision using the ADVANPIX Multiprecision Computing Toolbox for Matlab (https://www.advanpix.com/); test_time.m which times the execution of wTrap.m against other publicly available, published codes for evaluation w(z); test_accuracy_Q.m which tests the accuracy of wTrap.m and the accuracy of the same other publicly available Matlab codes against the quadruple precision version wTrap_Q.m.

For more details of all these codes see [2].

Mohammad Al Azah (Al Hussein Technical University, Amman, Jordan) and
Simon Chandler-Wilde (University of Reading, UK)

[1] M. Al Azah and S. N. Chandler-Wilde, Computation of the complex error function using modified trapezoidal rules, 2021, https://arxiv.org/abs/2010.05659 . To appear in SIAM Journal on Numerical Analysis.

[2] M. Al Azah and S. N. Chandler-Wilde, Supplementary Materials: Computation of the complex error function using modified trapezoidal rules, 2021, http://www.personal.rdg.ac.uk/~sms03snc/#respre . To appear (as supplementary materials to [1]) in SIAM Journal on Numerical Analysis.
