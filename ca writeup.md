### Ufuks comments

- [X] A figure that explain the setting for the collision avoidance would be good. It can be used to explain regions of interest, operating regions, intersection, etc.
- [X] Intention?
- [X] Resolving intersection?
- [ ] The collision avoidance animation is not that useful. Annotate maybe somehow?
- [X] How much can you scale at this point (layers, vehicles etc.)? 
- [X] Make another example with a larger (or largest you can). 
- [X] VIP: needs details, figure.
- [X] What is location? 
- [X] What does escorted mean? 
- [X] Inspect? 
- [X] Route? 
- [X] Of interest? 
- [X] Unsafe? 
- [X] Zone? 
- [X] Specs?
- [X] Write sentences! 

# Examples

## Synthesis Collision Avoidance Protocol 

### Problem statement

In this scenario we have multiple UAVs, altitude layers and locations of interest. a UAV can ascend or descend to the altitude layer above or below its current altitude layer. A location of interest is a predefined location on an altitude layer. Our aim is to automatically synthesize a control protocol that guarantees the following:

1. Each UAV is able to visit -infinitely often- any of the locations of interest. 
2. A UAV must not collide with any other UAV. 

### Approach 

Our approach to this problem is centered around the idea of UAVs' operating regions. An operating region for a UAV is a polygon on the UAV's current altitude layer. We assume That the UAV will only fly within its operating region. With this assumption, we can guarantee that no collision will happen if the UAV(s) with intersected operating(s) remain still until the intersection is resolved. 

### Problem Setup

We model this problem by assigning three output variables $l_{i}$, $p_{i}$, $t_{i}$ and $(n-1)$ input variables $c_{ij}$ to each $UAV_{i}$. The variables are defined as follows:
- $l_{i} \in L$ the set of layers : the altitude layer for $UAV_{i}$ to ascend or descend to.

- $p_{i} \in P$ the set of location of interest : the location of interest for $UAV_{i}$ to head to.

- $t_{i} \in T$ the set of location of interest : the intention of $UAV_{i}$.

- $c_{ij} \in B$ the boolean set : true if the operating region for $UAV_{i}$ intersects with that of $UAV_{j}$ and false otherwise. 

At each time instance, the synthesized controller takes the variables $c_{ij}$ as inputs then determines $l_{i}$, $g_{i}$, $t_{i}$ for each UAV.

### System specifications

- $UAV_{i}$ can only go to the locations that are in the same altitude layer
    - $(\bigwedge G (l_{i} = x \implies g_{i} = x \bigvee g_{i} = n))$

- $UAV_{i}$ and $UAV_{j}$ must not be at the same altitude layer if $c_{ij}$ is true (their operating regions intersect).
    - $(\bigwedge \bigwedge G (c_{ij} \implies l_{i} \neq l_{j}))$ 

- If $UAV_{i}$ is given a command to go to $x$ then it must have signaled its intent at the previous step.
    - $(\bigwedge G (o p_{i} = x \implies t_{i} = x))$

- $UAV_{i}$ will eventually be sent the command to go to $x$
    - $(\bigwedge F (p_{i} = x))$

### Environment assumptions

We assume that if two UAVs have intersecting operating regions and one of the UAVs signaled an intention to go to a location then the intersection will be resolved:
[still working on this spec for now it's simply $\bigwedge (F \neg c_{ij})$]

### Demo

[Here I will show a set of figures and describe what's going on]
