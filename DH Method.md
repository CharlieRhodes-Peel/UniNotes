# Denavit Hartenberg (DH) Method
Assumes each joint is either revolute or prismatic
#### How To Pick Reference Frames
1. Each Z-axis passes THROUGH a join
2. The $X_i$ axis is perpendicular to $Z_{i-1}$ axis
3. The $X_i$ axis **intersects** the $Z_{i-1}$ axis
4. The $Y_i$ axis is then determined by the choice of the previous

# Order for DH REMEMBER THIS!
![[Pasted image 20260111095732.png]]
Rot trans, trans rot!
and it goes zi-1, zi-1. xi, xi
- Z behind, z behind, x infront, x infront
- Variables = odaa !! remember odaa
- and if it's rot, trans, trans rot then odaa would be:
	- $\theta d a \alpha$


# DH Procedure:
1. Assume a robot has $n$ joints and thus $n+1$ links
2. Join $i$ connects link $i-1$ and Link $i$
3. The $i-1$th reference frame $F_{i-1}$ is located on the Joint $i$
4. The $Z_{i-1}$ axis passes through Joint $i$
5. Each joint is either prismatic (d variable) or revolute ($\theta_i$ variable)
6. The base frame is assigned first: this is essentially arbitrary
7. Each reference frame is determined sequentially such that the next x is perp to it's previous z axis
8. Determine the 4 DH parameters
	1. $\theta_i$ Joint angle between link i-1 and link i (angle around $Z_{i-1}$) GO ANTI CLOCKWISE!!!!!
	2. $d_i$ Link offset, distance between Origin of $Z_{i-1}$ and it's intersection with $X_i$
	3. $a_i$ link length; Distance **along** $X_i$ between Z behind and Z infront
	4. $\alpha_i$ Twist offset. Essentially angle between the $Z_{i-1} - X_{i-1}$ and $Z_{i} - X_{i}$ planes