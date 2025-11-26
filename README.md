# simulated-annealing-salesman
We can use our simulated annealing approach to search only among tours that satisfy the constraint, so we want to have the tours where all cities within a given country appear consecutively. We can do this by breaking up a tour into two parts:

The ordering of the $P$ countries, which determines the order in which the salesman visits the countries.
Then for each country, an ordering of the cities in that country, which is just a tour of that country.

The complete tour is then obtained by concatenating the inter-country tours following the order of the countries. Then we gradually decrease temperature so that we can concentrate on tours with lower total cost.

Our method will be as follows, we have $N+1$ cities and we have a distance matrix $D$ that represents our cost that we have for the distances between cities. Since not all the possible tours are realistic for our problem, we can have our initial tour be where the countries are randomly ordered and within each country, the cities are randomly ordered to create a random tour permutation.

To explore new solutions, we can have two types of moves:

First between countries, we can randomly pick two countries and swap their order in the tour. This changes the sequence in which countries are visited, however we keep the same ordering of the cities within each country.
Then within a country, we can randomly pick two cities within the same country and swap their positions. This would be our way to optimize the ordering of cities within a country, which is like a cluster-based approach.

Then we can use our simulated annealing approach so that we provide a metric with a proposed solution, where if the new solution has a lower cost, it is always accepted. If the new solution has a higher cost, it is accepted with probability $e^{\frac{-\Delta E}{T}}$, which allows us to escape from local minima. With this method we can probably efficiently search our space and hopefully find an optimal tour with the lowest computed cost.\
