
### Setup Time Constraint
$$T_c \geq t_{pcq}+t_{pd}+t_{setup}+t_{skew}$$

$$T_c \geq t_{setup}+\text{max delay (FF)+max delay(combinational)} + skew$$

### Hold Time Constraint

$$t_{hold} < \text{min delay (FF)+min delay(combinational)} - skew$$
$$t_{hold} < t_{ccq}+t_{cd}-t_{skew}$$

# Definitions
### Combinational

### $t_{cd}$ 
Contamination Delay
Minimum delay
# $t_{pd}$
Propagation delay
Maximum delay
### Sequential
![[Pasted image 20260303203228.png]]

If we can guarantee constant D signal within the $t_a$ range of the rising clock edge, we can guarantee no error.

![[Pasted image 20260303210202.png]]

