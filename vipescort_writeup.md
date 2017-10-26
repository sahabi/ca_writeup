## VIP Escort 

### Problem statement

In this scenario we have one main UAV we call "VIP", multiple "escort" UAVs, multiple pre-defined locations of interest. Our aim is to automatically synthesize a control protocol that guarantees the following:

1. The VIP must not move from one location to another without being escorted by one of the escorts. 
2. The VIP cannot visit certain locations until at least one of the escorts have inspected the location within the last $x$ steps. 
3. All the UAVs must go through a certain route to the location of interest. This is needed to prevent going through unsafe zones.


### Problem Setup

We model this problem by assigning two output variables $g_{i}$ and $t_{i}$ and one input variables $s_{i}$ to each escort $UAV_{i}$. The variables are defined as follows:

### System specifications

### Environment assumptions

### Demo

[Here I will show a set of figures and describe what's going on]
