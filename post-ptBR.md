# Uma breve introdução aos Algoritmos Genéticos

Um algoritmo genético é uma metaheurística inspirada no processo de seleção natural, e pertence a uma grande família de algoritmos evolucionários

De acordo com a seleção natural de Darwin: *Indíviduos com traços adequados para sobreviver à luta por recursos deve contribuir com mais decendentes na próxima geração*.

As the Darwin's natural selection says: *Individuals possessing traits well suited for the struggle for local resources will contribute more offspring to the next generation*. That is, if we could figure out a way to express the competition and measure it, .

There is a theorem called [Infinite Monkey](https://whatis.techtarget.com/definition/Infinite-Monkey-Theorem). It says that an unlimited number of monkeys will eventually produce a text, such as Shakespere's *Romeo and Juliet*, given typewriters and sufficient time. We can model it as a Genetic Algorithm:

## Phases

### Initialization and Fitness Score

The fitness score is basically how close the population is to archive its aim. In our algorithm, we want it to generate the target sentence. So, we'll use the difference between characters as our score.

```python
def calculate_fitness(individual, target_genotype):
    fitness = 0
    for individual_gene, target_gene in zip(individual.genotype, target_genotype):
        if individual_gene != target_gene: fitness+= 1
    return fitness
```

### Selection

### Crossover and Mutation

With the parents selected, the crossover phase can start. Basically we will randomily select each of the offspring genes from one of its parents. Also, a mutation rate is applied. It will generate a random gene from our poll, when requested.

```python
for parent1_gene, parent2_gene in zip(parent1.genotype, parent2.genotype):

  # random probability
  probability = random.random()

  # Crossover
  if probability < self_gene_threshold:
    child_genotype.append(parent1_gene)
  elif probability < partner_gene_threshold:
    child_genotype.append(parent2_gene)

  # Mutation
  else:
    child_genotype.append(self.__generate_mutated_gene())
```

## References

* https://en.wikipedia.org/wiki/Genetic_algorithm
* https://www.geeksforgeeks.org/genetic-algorithms/