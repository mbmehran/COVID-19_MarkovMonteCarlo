# COVID-19_MonteCarlo

Monte Carlo (MC) simulation to measure how outbreaks such as the COVID-19 virus can spread.

## Simple Model:
In the simple version of this COVID-19 outbreak simulation we only use few variables aming to describe epidemic effect for general audience similir to Harry Stevens [work](https://www.washingtonpost.com/graphics/2020/world/corona-simulator/?fbclid=IwAR0LrA8mFe_8tZTsliPL8mBIac7qOpEuN_xAAYfTluH-GvCN8bor2pPSX5A&utm_campaign=wp_main&utm_medium=social&utm_source=facebook).
However, I want to give reader more tangable defintion for social distance and personal hygiene
avoid any underestimation during this outbreak. Please note that our model is a rough/simplified representaion of outbreaks and to draw any solid conclusion for policy maker more sofistikated model is needed.

__Social distacne__ describe/control the average number of people that one person in the society is in contact (eigther __directly__ or __indirectly__ via mediator such as touching somthing which is touched by the others) __per week__. For instance, in the normal situation (low social distance) that you go to work, take public transit, shopping, bar, family/friends gathering this number can easily reach 50 (considering indirect contacts).

__personal hygeine__ such as hand-washing, describe beside virus contigous which is really high for COVID-19. 

Here are parameters considered to describe the system: 
- N_c : __Average number of contact per week per person__  
- T_r : __Transmision rate__               ()
_ P_s : Time takes for the symthoms to appears
- P_r : Time takes for recovery
- N_0 : Initial Number of sick people (people who are infected but not isolatd at time=0)
- F_r : Fatality rate, probability of person who is in in recovery mode die.

Assumption:
- people who aware of their disease (eigther confirmed cases or cases with symptoms) do not trasnmit virus anymore (Self-isolation)
- people after recovery still may get the disease
- Ideal cases: 
  - no limit in supply for self-isolation
  - no limit in number for recovery (hostipital can be full ...)
  - ...
