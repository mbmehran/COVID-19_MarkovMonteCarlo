# COVID-19_MonteCarlo
I used Markov Chain Monte Carlo (MCMC) simulation to represent how outbreaks such as the COVID-19 epidemic can spread.
[Simulated source code will be posted soon]

## Simple Model:
In the simple version of this COVID-19 outbreak simulation, we only use few parameters aiming to describe epidemic effect for general audience and to raise awareness about "Social distancing" as well as "personal hygiene"; similar to Harry Steven's [work](https://www.washingtonpost.com/graphics/2020/world/corona-simulator/?fbclid=IwAR0LrA8mFe_8tZTsliPL8mBIac7qOpEuN_xAAYfTluH-GvCN8bor2pPSX5A&utm_campaign=wp_main&utm_medium=social&utm_source=facebook). Here, I tried to give readers more tangible definition/metrics for the social distance and personal hygiene to avoid any underestimation during this infectious disease outbreaks. 

__Social distance__ would describe/control the average number of people that one person in the society would be in close contact with __ either __directly__ or __indirectly__ (i.e. via a mediator object such as touching something which has been touched by the others before). In the normal situation (low social distance) when you go to work regularly, you use public transit, do shopping, go to bars/restaurants as well as family/friends gathering, thus, the __average number of contacts per week (N_c)__ can easily go beyond 100 (considering indirect contacts).

__Personal hygiene__ such as hand washing and etc, would describe/control __T_r transmission rate__ odds of getting infected, if you were exposed to the virus carrier (i.e. person or object containing virus). For highly contagious virus such as COVID-19, the transmission rate could be as high as 50%; however, with all warnings and precautionary steps that one with high personal hygiene may take, one can reduce the transmission rate to less than 10%.


### Model Details
Let's consider a society of 1000 individuals where only 5 members have been infected. Now, we want to describe how the disease would spread based on the virus ''transmission rate'' and "average number of times per week that an individual will be in close contact (directly or indirectly) with other members".
Here, we assume
 1) Infected members can transmit the virus, with respect to the given transmission rate, to their healthy connections within a first two weeks (latent stage)
 2) After two weeks, the infected person will be isolated (not transmitting) for three weeks to recover.  
 3) Not every one would survive and odds of failure in recovery (death) is 2%.
 4) If survived, recovered members will get back into healthy population but their transmitting rate reduces to 2%.

Here are simulation parameters:
- N_c : __Average number of contacts per week per person__  
- T_r : __Transmission rate__; (odds of getting infected if you were exposed to the virus carrier)              
- P_t : __Period of transmission__; (During this period, infected person will be in contact with others and transmit the virus at the rate of T_r to their connections. It is set to two weeks, starting the infection date; similar to time that takes for the symptoms to appear in infected person. )
- P_r : __Period of Recovery__ (Set to three weeks, starting appearance of symptoms. during this period, infected person is isolated for three weeks to get well and cannot transmit the virus)
- N   : System population (Set to 1000)
- N_0 : Initial Number of sick people (people who are infected but not isolated at time=0; set to 5)
- F_r : Fatality rate; probability of one cannot be recovered and die.
- TrR : Transmitting rate after recovery, set to 2%

We create network systems of N nodes which are randomly connected in a way that members have, on average, N_c connections. Then, we randomly select N_0 of those nodes and put them into Infected mode capable of transmitting the disease. Through weekly iterations, we update the system with respect to T_r, TrR, P_t, P_r, and F_r, explained above. Infected nodes have two weeks (two time-steps) from beginning of their infection to transmit the virus with the rate/probability of T_r to their connections. After two weeks infected nodes are isolated for three weeks to recover. They may die with fatality rate of F_r. If they survive, they will get back into healthy population but their transmitting rate reduce to TrR. 20 different network systems are created and average results and corresponding STD are reported below.

 
### Results
Now we can simulate the outbreaks and investigate the spreading curve of disease with respect to "the average number of contacts per week for netwroks members" and "disease transmission rate". Note that in any circumstances, people still need to do grocery shopping and not everyone is able to work from home (N_c >= 1).  

__Let's flatten the cure__
 
High Social-distance (N_c = 10)<br> Various transmission rates (T_r) | High Personal hygeine(T_r = 5%)<br> Various number of contacts (N_c)
:---------------------:|:---------------------:
<img src="https://github.com/mbmehran/COVID-19_MarkovMonteCarlo/blob/master/common/Tr4.gif" width="400" height="400" /> | <img src="https://github.com/mbmehran/COVID-19_MarkovMonteCarlo/blob/master/common/Nc4.gif" width="400" height="400" />

Although we simulate the spread of a fake disease through a population, yet it would capture essential feature of real case. As one can see shape of the spreading curve is controlled by T_r and N_c. (N_0 only dictate when curve should occurs and does make any noticeable differences in shape of the curve; data not shown).

__As a result, even if one thinks that with taking extra precautionary steps we can make the transmission rate of this contagious disease as low as 5%, people still should not be in close contact with more than 10-12 persons per week on average.__

### This is oversimplified model:
- Network with static connections: connections are fixed and new connections cannot be created.
- no limit in number of people in self-isolation
- no limit in number of people under recovery (unlimited capacity for healthcare system)  
- ...

#### Disclaimer: 
Please note that our model is a rough/oversimplified representation of such outbreak and to draw any solid conclusion and measurements for policy makers, a more sophisticated model is needed. However, our model is able to show critical features of infectious disease outbreaks such as covid-19.

