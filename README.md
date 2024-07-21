
# SalesPath

The Traveling Salesman Problem statement is as follows: Given a list of cities and the distances between each pair of cities, what is the shortest possible route that visits each city exactly once and returns to the origin city?
We want the shortest tour. It can’t be solved in polynomial time (NP-Hard) because suppose there are 19 cities, then I have 19 choices of which one to visit first, 18 choices of which one to visit second, …, 1 choice of which one to visit at last. In total, that’s 19! possibilities and if I have a computer that can test 1 billion tours per second, it’s going to take 19! / 1,000,000,000 ~ 3.85 years to finish. Therefore, I will use Genetic Algorithm and Google Maps API to solve and visualize this problem.



The Traveling Salesman Problem (TSP) aims to find the shortest route that visits each city exactly once and returns to the starting city. Given its factorial complexity (N!), GA provides a heuristic approach by mimicking natural selection and genetics.

Initialization: Begin with a population of random sequences representing different city visit orders. Each sequence's fitness is evaluated based on the total distance traveled, where shorter routes indicate higher fitness.

Fitness Calculation: Evaluate each sequence's fitness by computing the total distance traveled. This step quantifies how well each sequence optimizes the route.

Selection: Use a selection mechanism favoring sequences with higher fitness, similar to natural selection. Fitter sequences have a greater chance of being selected for reproduction (crossover).

Crossover: Breed new sequences (offspring) by combining parts of two parent sequences. Select crossover points and swap segments to potentially create better solutions.

Mutation: Introduce random mutations in offspring to maintain genetic diversity and explore different parts of the solution space. This prevents premature convergence to suboptimal solutions.

Iteration: Repeat the selection, crossover, and mutation steps for multiple iterations (generations). This iterative process evolves the population toward better solutions over time.

Final Solution: After a fixed number of iterations, select the fittest sequence from the final population as the optimal route for the TSP. This sequence represents the shortest possible route visiting each city once and returning to the starting city.

Implementing this approach with the Google Maps API involves geocoding to convert city names or addresses into geographical coordinates, calculating distances between cities, and visually presenting the optimal route on a map interface. Each city input corresponds to a waypoint in the TSP solution, demonstrating the effectiveness of GA and APIs in solving complex optimization problems.