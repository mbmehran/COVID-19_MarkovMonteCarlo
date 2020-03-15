# COVID-19_MarkovMonteCarlo

Markov Chain Monte Carlo (MCMC) simulation for the COVID-19 epidemic.

## Simple Model:
In the simple version of MCMC simulation model we used few parameters and we are aiming to
leani epidemic curve and its evolution corresponding to civilians behaviour. 

Here are parameters considered for to describe the system: 

- C_m : Average  number of contact per week per person
- P_t : Probability of the virus transmition for people in contac
_ T_s : Time takes for the symthoms to appears
- T_r : Time takes for recovery
- N_0 : Initial Number of transmitor (people who are infected but not isolatd at time=0)
- F_r : Fatality rate/probability 

Assumption:
- people who aware of their disease (eigther confirmed cases or cases with symptoms) do not trasnmit virus anymore (Self-isolation)
- people after recovery still may get the disease
- Ideal cases: 
  - no limit in supply for self-isolation
  - no limit in number for recovery (hostipital can be full ...)
  - ...
