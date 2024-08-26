# FDM

Finite Difference Methods (FDM) are numerical techniques for solving differential equations by approximating them with difference equations. These methods involve discretizing a continuous domain (e.g., time or space) into a grid and approximating derivatives by using differences between function values at grid points.

1. Discretization
Consider a function u(x, t) that depends on space x and time t. In finite difference methods, both x and t are discretized:

Let x_i = i * Delta_x where i = 0, 1, 2, ..., N.
Let t_n = n * Delta_t where n = 0, 1, 2, ..., M.
Here, Delta_x is the spatial step size, and Delta_t is the time step size.

2. Approximation of Derivatives
   
A) First-Order Derivative (Time or Space)
For the first-order derivative with respect to x:
1) Forward Difference:
du/dx ≈ (u(x_{i+1}, t) - u(x_i, t)) / Delta_x
2) Backward Difference:
du/dx ≈ (u(x_i, t) - u(x_{i-1}, t)) / Delta_x
3) Central Difference:
du/dx ≈ (u(x_{i+1}, t) - u(x_{i-1}, t)) / (2 * Delta_x)

B) Second-Order Derivative 
For the second-order derivative with respect to x (space):
d²u/dx² ≈ (u(x_{i+1}, t) - 2 * u(x_i, t) + u(x_{i-1}, t)) / Delta_x²

3. The 1D Heat Equation
The 1D heat equation is a common PDE given by:
du/dt = alpha * d²u/dx²
where alpha is the thermal diffusivity.

The explicit finite difference method approximates this equation as follows:
1) Discretization:
Let u_i^n denote the approximation to u(x_i, t_n), where i and n correspond to space and time steps, respectively.
2) Finite Difference Approximation:
(u_i^{n+1} - u_i^n) / Delta_t = alpha * (u_{i+1}^n - 2 * u_i^n + u_{i-1}^n) / Delta_x²
3) Solving for the next time step n+1:
u_i^{n+1} = u_i^n + (alpha * Delta_t / Delta_x²) * (u_{i+1}^n - 2 * u_i^n + u_{i-1}^n)


4. Stability Condition for the Explicit Method
The explicit method has a stability condition given by:
alpha * Delta_t / Delta_x² <= 1/2
If this condition is not met, the numerical solution may become unstable.

The implicit method, specifically the Crank-Nicolson scheme, is unconditionally stable and can be written as:
(u_i^{n+1} - u_i^n) / Delta_t = (alpha/2) * ((u_{i+1}^{n+1} - 2 * u_i^{n+1} + u_{i-1}^{n+1}) / Delta_x² + (u_{i+1}^n - 2 * u_i^n + u_{i-1}^n) / Delta_x²)

Rearranging for a system of linear equations to solve at each time step:
-(alpha * Delta_t / 2 * Delta_x²) * u_{i-1}^{n+1} + (1 + alpha * Delta_t / Delta_x²) * u_i^{n+1} - (alpha * Delta_t / 2 * Delta_x²) * u_{i+1}^{n+1} 
= (alpha * Delta_t / 2 * Delta_x²) * u_{i-1}^n + (1 - alpha * Delta_t / Delta
