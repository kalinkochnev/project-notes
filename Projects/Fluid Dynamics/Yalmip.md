## Yalmip
### usage/syntax
`sdpvar` is a symbolic decision variable that yalmip uses as constraints
- most matlab operators are defined for sdpvar objects

ex: symmetrix matrix
```
P = sdpvar(n,n) % SYMMETRIC!
```

ex: diagonal matrix
```
X = diag(sdpvar(n,1));
```

#### Error codes
https://yalmip.github.io/command/yalmiperror/
### computing decay rate of LTI system with GEVP
https://yalmip.github.io/example/decayrate/
- Problem is quasi-convex (feasible set scales monotonically), solves using bisection
	- Set a lower/upper bound on lambda (programmer decides)
	- Begin bisection. Checks values between lower/upper bound. If it is feasible it updates the lower bound.

==Note don't need to code bisection ourselves, just use `bisection()` solver==
Can compute the lower bound
```
A = [-1 2; -3 -4];
P = sdpvar(2, 2); // symmetric 2x2 matrix

// Lower bound P so it is positive semidefinite (with some offset if desired)
// Constraint A^T P + PA <= -identity
Constraints = [P >= eye(2), A' * P + P*A]

optimize(Constraints, trace(P)) // minimize the trace 

// can solve for the eigenvalue
P0 = value(P);
t_lower = -max(eig(inv(P0)*(A'*P0+P0*A)))/2;
```


Can compute the upper bound
```
t_upper = t_lower*2;
F = [P>=eye(2), A'*P+P*A <= -2*t_upper*P];
ops = sdpsettings('verbose',0,'warning',0);
sol = optimize(F,[],ops);
while ~(sol.problem==1)
    t_upper = t_upper*2;
    F = [P>=eye(2), A'*P+P*A <= -2*t_upper*P];
    sol = optimize(F,[],ops);
end
```

#### Using preexisting bisection solver
```
sdpvar t
Constraints = [P>=eye(2), A'*P+P*A <= -2*t*P];
Objective = -t;
diagnostics = bisection(Constraints, Objective,sdpsettings('solver','mosek'))
```

