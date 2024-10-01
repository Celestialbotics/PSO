# Particle Swarm Optimization (PSO) Algorithm

### Input:
- **Objective function**: `f(x)` to minimize (or maximize)
- **Number of particles**: `N`
- **Maximum iterations**: `T`
- **Dimension of the search space**: `d`
- **Inertia weight**: `w`
- **Acceleration constants**: `c1`, `c2` (cognitive and social coefficients)
- **Upper and lower bounds of the search space**: `[xmin, xmax]`

### Initialize:
1. Initialize the position `Xi` and velocity `Vi` of each particle `i ∈ {1, 2, ..., N}` randomly within the search space.
2. Set the personal best position `pbest,i = Xi`.
3. Find the global best position `gbest` by evaluating all particles.
4. Define the velocity bounds `[Vmin, Vmax]`.

### Main loop (for each iteration `t`):
For each particle `i`:
1. **Update velocity**:
   \[
   Vi(t+1) = w \cdot Vi(t) + c1 \cdot r1 \cdot (pbest,i - Xi(t)) + c2 \cdot r2 \cdot (gbest - Xi(t))
   \]
   where `r1` and `r2` are random numbers in `[0, 1]`.

2. **Update position**:
   \[
   Xi(t+1) = Xi(t) + Vi(t+1)
   \]
   Ensure the new position is within the bounds `[xmin, xmax]` by clamping.

3. **Evaluate fitness** of the updated position:
   \[
   f(Xi(t+1))
   \]

4. **Update the personal best for each particle**:
   \[
   \text{if } f(Xi(t+1)) < f(pbest,i), \text{ then } pbest,i = Xi(t+1)
   \]

5. **Update the global best**:
   \[
   \text{if } f(pbest,i) < f(gbest), \text{ then } gbest = pbest,i
   \]

Repeat until the maximum number of iterations `T` is reached or the solution converges.

### Output:
- The global best position `gbest` and the associated fitness value.

### Key Parameters:
- **Inertia weight** `w`: Controls the impact of the previous velocity.
- **Cognitive coefficient** `c1`: Pulls the particle towards its own best-known position.
- **Social coefficient** `c2`: Pulls the particle towards the best-known position in the swarm.
