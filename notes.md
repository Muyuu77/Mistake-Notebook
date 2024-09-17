## Probability


MDP = (S,A,R,y1,P,u,H) 
S * A -> R 
y = [0,1) -> finite y = 1 
P: S*A -> det(S)

G_h = R1 + y*R2 + Y^2*R3 + ... + y^n-1*Rn

-> h = infinite 


value function -> ojective 

V_pai = E[Sum(y^h-1 * r_h) | s_0 ~ u, a_h~pai(s_h), s_h+1 ~ P(| s_h,a_h)]

V_pai(s) = E[sum(y_h-1 * r_h | s_0 = s, a_h~pai(s_h),s_h+1~P(| s_h,a_h)]

V_pai: S -> R 

Start in different states -> different rewards in the end?

Q(s,a) = E[sum(y_h-1 * r_h | s_0~u), a_0 = a, s_h+1~P(|s_h,a_h)]

Q: S*A -> R

Example:

s1 -> a1 -> s2 <br>
s1 -> a2 -> s3 

S = {s1,s2,s3}

A = {a1,a2}

P(s2|s1,a1) = 1 , P(s3|s1,a1) = 0 <br>
P(s3|s1,a2) = 1 , P(s2|s1,a1) = 0

R(s1,a1) = 1 <br> 
R(s1,a2) = 0

Pai = (0.5,0.5)

so:<br> 
Q(s1,a1) = 1 <br>
Q(s1,a2) = 0

V(u1) = V(s1) = 0.5

so pai_star = (1,0)





