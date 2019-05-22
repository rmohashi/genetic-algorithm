# Genetic Algorithm

Genetic Algorithms test repository

## Setup

1. Ensure you have [python3](https://www.python.org/) installed on your computer
1. If necessary, create a new environment (with *conda* or *pyenv*)

## Running

### Infinite Monkey

1. Set the constants:

    ```
    POPULATION_SIZE
    ELITISM_RATE
    SELECTION_SIZE
    MUTATION_RATE
    ```
1. Set the `DEFAULT_TARGET` as the desired sentence
1. Run:

   ```bash
   python infinite_monkey.py
   ```

### Sonic NEAT

1. Install dependencies:

    ```
    pip install neat-python
    pip install numpy
    pip install gym-retro
    pip install opencv-python
    ```
1. Get a copy of the ROM
1. Place the ROM file inside the `retro` installation folder, under `data/stable/SonicTheHedgehog2-Genesis`
1. Run:

    ```bash
    python sonic_hedgehog_2.py
    ```