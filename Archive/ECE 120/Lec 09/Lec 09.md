![[ECE 120/Lec 09/images/1.png|300]]: $Q=A'$  
![[ECE 120/Lec 09/images/2.png|300]]: NOR: $(A+B)'$  
![[images/Pasted image 20230203083044 1.png|300]]: NAND: $(AB)'$  

## Optimizing Logic Expression
> Choose a metric First  

How do we measure good?  
- area / size / cost,                     or  
- performance / speed,              or
- power / energy consumption, or  
- complexity / reliability.

measuring exactly is expensive, so instead we use **heuristics** which are ways of **estimation metric**  

heuristics for area:  
- Count literals (A, A', B, B', C, C'),  then  
- Add the number of operations (not including complements for literals).  
Why:  
- each input (literal) -> 2 transistors  
- operators into operators -> 2 transistors  
Thus, it gives an approximate **transistor count**.  
(But wires also take some space)  

heuristic for daylay / speed:  
- Find the maimum number of gates betweeen any input and any output.  
- Do not include complements for literals.  
Why:  
- Each gate takes time switch its output on/off.  
- We call this time a gate delay.  

one heuristic for power