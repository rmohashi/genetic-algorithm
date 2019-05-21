# A brief introduction to Genetic Algorithms

<!-- Image - Darwin -->

A genetic algorithm is a metaheuristic inspired by the process of natural selection that belongs to the larger class of evolutionary algorithms. They are well suited for otimization and search problems.

As Darwin's natural selection says: *Individuals possessing traits well suited for the struggle for local resources will contribute more offspring to the next generation. Because of that, helpful traits tend to become more common in the next generations and the population will become adapted to its environment*.

In genetic algorithms, these traits can be measured by the **fitness score**. It is basically how close the population is to archive its aim. The less a fitness value is, the closer to the final solution.

Let's see how it works in practice.

## Infinite Monkey

<!-- Image - monkeys -->

There is a theorem called [Infinite Monkey](https://whatis.techtarget.com/definition/Infinite-Monkey-Theorem). It says that an unlimited number of monkeys will eventually produce a text, such as Shakespere's *Hemlet*, given typewriters and sufficient time. We can model it as a Genetic Algorithm.

### Initialization and Fitness Score

First of all, we need a initial population. It will be generated randomly selecting the genes from our poll, and then, the fitness score is calculated for each individual.

In our algorithm, we want it to generate the target sentence. The will be the difference between characters as our score.

```python
def calculate_fitness(individual, target_genotype):
    fitness = 0
    for individual_gene, target_gene in zip(individual.genotype, target_genotype):
        if individual_gene != target_gene: fitness+= 1
    return fitness
```

### Selection

As explained before, the individuals with well suited traits will contribute more offspring. To accomplish it, the population is sorted according to the fitness score.

```python
population = sorted(population, key = lambda x: x.fitness)
```

The less fit part of the population won't leave any descendants and the genes will disappear.

```python
for _ in range(generated_individuals_size):
    parent_1 = random.choice(population[:SELECTION_SIZE])
    parent_2 = random.choice(population[:SELECTION_SIZE])
    child = parent_1.reproduce(parent_2)
    new_generation.append(child)
```

### Crossing Over and Mutation

Parents selected, the crossing over phase can start. Basically we will randomly select each of the offspring genes from one of its parents. Also, a mutation rate is applied. It will get a random gene from our poll, when requested.

```python
for parent1_gene, parent2_gene in zip(parent1.genotype, parent2.genotype):

    # random probability
    probability = random.random()

    # Crossing Over
    if probability < self_gene_threshold:
        child_genotype.append(parent1_gene)
    elif probability < partner_gene_threshold:
        child_genotype.append(parent2_gene)

    # Mutation
    else:
        child_genotype.append(self.__generate_mutated_gene())
```

Finally, let's run the code:

<script src="https://gist.github.com/rmohashi/be36f9d346dea115bc157a04f6b88f5d.js"></script>

<!-- GIF - execution -->

It works! :tada: :tada:

## Genetic Algorithm in Neural Networks? Welcome NEAT

What about applying the concept of genetic algorithms in neural networks? That is exactly what the algorithm Neuroevolution of Augmenting Topologies, or simply NEAT, does. Insted of relying on fixed size neural nets, it evolves the model to fit the target.

There is a Python library called [neat-python](https://github.com/CodeReclaimers/neat-python) that implements the algorithm. Using it with [retro](https://github.com/openai/retro), we could train our model to play a game.

I've trained the model to beat a single stage of the game [Sonic the Hedgehog 2](https://store.steampowered.com/app/71163/Sonic_The_Hedgehog_2/).

<!-- GIF: Sonic -->

## References

* https://www.khanacademy.org/science/biology/her/evolution-and-natural-selection/a/darwin-evolution-natural-selection
* https://en.wikipedia.org/wiki/Genetic_algorithm
* https://www.geeksforgeeks.org/genetic-algorithms/
* https://towardsdatascience.com/neat-an-awesome-approach-to-neuroevolution-3eca5cc7930f