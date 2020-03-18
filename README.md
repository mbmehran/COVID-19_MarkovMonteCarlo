# COVID-19_MonteCarlo
Markov Chain Monte Carlo (MCMC) simulation to represent how outbreaks such as the COVID-19 epidemic can spread.
[Simulated source code will be posted soon.]

## Simple Model:
In the simple version of this COVID-19 outbreak simulation we only use few variables aiming to describe epidemic effect for general audience and raise awareness about "Social distancing" as well as personal hygiene; similar to Harry Steven's [work](https://www.washingtonpost.com/graphics/2020/world/corona-simulator/?fbclid=IwAR0LrA8mFe_8tZTsliPL8mBIac7qOpEuN_xAAYfTluH-GvCN8bor2pPSX5A&utm_campaign=wp_main&utm_medium=social&utm_source=facebook). However, I want to give readers more tangible definition/metric for the social distance and personal hygiene to avoid any underestimation during this infectious disease outbreaks. 

__Social distance__ describes/controls the average number of people that one person in the society would be in close contact__ either __directly__ or __indirectly__ (i.e. via a mediator object such as touching something which has been touched by the others before). In the normal situation (low social distance) when you go to work regularly, use public transit, do shopping, bars/restaurants, family/friends gathering, the __average number of contacts per week (N_c)__ can easily go beyond 100 (considering indirect contacts).

__Personal hygiene such as hand washing and etc, describes/controls __T_r transmission rate__ odds of getting infected if you were exposed to the virus carrier (i.e. person or object containing virus). For highly contagious virus such as COVID-19 transmission rate maybe as high as 50%; however, with all warning and precautionary steps that one with high personal hygiene may takes, one can reduce it to less than 10%.


### Model Details
Now lets take a look at parameters which describe our simulation system:
- N_c : __Average number of contacts per week per person__  
- T_r : __Transmission rate__; (odds of getting infected if you were exposed to the virus carrier)              
_ P_t : __Period of transmission__; (Set to two weeks starting the infection date; similar to time which takes for the symptoms to appear in infected person. During this period infected person will be in contact with others and transmit the virus with the rate of T_r to their connections)
- P_r : __Period of Recovery__ (Set to three weeks starting appearance of symptoms. during this period infected person is isolated for three weeks to get well and cannot transmit the virus)
- N   : system population (Set to 1000)
- N_0 : Initial Number of sick people (people who are infected but not isolated at time=0; set to 5)
- F_r : Fatality rate; probability of one cannot be recovered and die.

We create a netwrok of N node which are randomly connected to have on average N_c conections. Then, randomly select N_0 of those nodes and enable them for tranmiting the virus. Through weekly iteration with updates the system with respects to T_r, P_t, P_r, and F_r explain above. Infected nodes have two weeks (two time step) from begining of their infection to transmit the virus with the rate/probability of T_r to their connections. After two weeks infected noded isolated for three weeks and not able to transmit the virus. They may die with fatality rate of F_r or recover and get back to healthy population but their transmitting rate reduce to 2%. We 20 different netwrok system are randomly created the network system and corresponding mean and std(shadow) are reported as results.

 
### Results
Now we can simulate the outbreaks and investigate how the virus spread with respect to the average number of contacts per week for each person and transmission rate. Following shows how virus spreads when one variable is in its most optimum possible value and the other varies. Note that in any circumstances, people still need to do grocery shopping and not everyone is able to work from home. So I approximate average number of contact for a society N_c = 10 as high social distance. 

High Social-distance (N_c = 10)<br> Various transmission rates (T_r) | High Personal hygeine(T_r = 5%)<br> Various number of contacts (N_c)
:---------------------:|:---------------------:
<img src="https://github.com/mbmehran/COVID-19_MarkovMonteCarlo/blob/master/common/Tr2.gif" width="400" height="400" /> | <img src="https://github.com/mbmehran/COVID-19_MarkovMonteCarlo/blob/master/common/Nc2.gif" width="400" height="400" />

if we consider that society would collapse when 20% of its population get infected, above results clearly show that number of contact per week should stay less than 13 even if one can decrease transmission rate down to 5%. 

### This is oversimplified model yet :
- Static network: connections are fixed and new connection cannot be created.
- no limit in supply for self-isolation
- no limit in number of people under recovery (unlimited capacity for healthcare system)  
- ...

#### Disclaimer: 
Please note that our model is a rough/oversimplified representation of such outbreak and to draw any solid conclusion and measurements for policy maker more sophisticated model is needed. However, our model able shows critical feature of infectious disease outbreaks such as covid-19.
