# COVID-19_MonteCarlo
Monte Carlo (MC) simulation to measure how outbreaks such as the COVID-19 virus can spread.

## Simple Model:
In the simple version of this COVID-19 outbreak simulation we only use few variables aiming to describe epidemic effect for general audience similar to Harry Steven's [work](https://www.washingtonpost.com/graphics/2020/world/corona-simulator/?fbclid=IwAR0LrA8mFe_8tZTsliPL8mBIac7qOpEuN_xAAYfTluH-GvCN8bor2pPSX5A&utm_campaign=wp_main&utm_medium=social&utm_source=facebook). However, I want to give reader more tangible definition for social distance and personal hygieneavoid any underestimation during this outbreak. 

__Social distance__ describe/control the __N_c: average number of people that one person in the society is in contact__ (either __directly__ or __indirectly__ via mediator such as touching something which is touched by the others) __per week__. For instance, in the normal situation (low social distance) that you go to work, take public transit, shopping, bar, family/friends gathering this number can easily reach 50 (considering indirect contacts). Note that in any circumstances, people still need to do grocery shopping and not everyone is able to work from home. 

__Personal hygiene such as hand washing, describe/control __T_r (transmission rate: odds of getting infected if you were exposed to the virus carrier__ (be in contact with an infected person or object). For highly contagious virus such as COVID-19 transmission rate maybe as high maybe about 80%; however, with all warning and precautionary step that one with high personal hygiene may be able to decrease it to less than 10%.


### Model Details
Here are parameters considered to describe the system:
- N_c : __Average number of contact per week per person__  
- T_r : __Transmission rate__ (odds of getting infected if you were exposed to the virus carrier)              
_ P_t : Transmitting period; time which takes for the symptoms to appear in infected person (Set to two weeks starting the infection day. During this period infected person will be in contact with others and enable transmitting the virus with the rate of T_r)
- P_r : Recovery period (Set to three weeks starting appearance of symptoms. during this period infected person is isolated for three weeks to get well and cannot transmit the virus)
- N   : system population (set to 1000)
- N_0 : Initial Number of sick people (people who are infected but not isolated at time=0; set to 5)
- F_r : Fatality rate; probability of one cannot be recovered and die.

We create a netwrok of N node which are randomly connected to have on average N_c connections. Then, randomly select N_0 of those nodes and enable them for tranmiting the virus. Through weekly iteration with updates the system with respects to T_r, P_t, P_r, and F_r explain above. Infected nodes have two weeks (two time step) from begining of their infection to transmit the virus with the rate/probability of T_r to their connections. After two weeks infected noded isolated for three weeks and not able to transmit the virus. They may die with rate/probability of F_r or recover and get back to healthy population.

### Results
Now we can simulate the outbreaks and investigate how virus spread with respect to the average number of contacts per week for each person and transmission rate. Following shows how virus spreads for 
- 1) N_c = 10 (high Social-distance) and different transmission rates T_r, 

![alt text](https://github.com/mbmehran/COVID-19_MarkovMonteCarlo/common/Tr.gif "Logo Title Text 1")

- 2) T_r = 5% (high Personal hygeine ) and different number of contact N_c


if we consider that society would collapse when 20% of its population get infected, above results clearly show that number of contact per week should stay less than 13 even if one can decrease transmission rate down to 5%. 

### This is oversimplified model yet :
- Recovered pationet can get infected again with same rate as others
- no limit in supply for self-isolation
- no limit in number for recovery (unlimited capacity for healthcare system)   

#### Disclaimer: 
Please note that our model is a rough/simplified representation of outbreaks and to draw any solid conclusion for policy maker more sophisticated model is needed. However, it shows critical feature of infectious disease outbreaks such as covid-19.
