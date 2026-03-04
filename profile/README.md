# VolPE
_Volunteer computing Platform for Evolutionary algorithms_

**VolPE** (Volunteer Computing Platform for Evolutionary Algorithms) is a distributed platform designed to solve complex optimization problems by harnessing the collective power of volunteer nodes. By utilizing a containerized **Island Model**, VolPE allows large-scale evolutionary experiments to run across heterogeneous environments, effectively turning a network of contributors into a massive parallel supercomputer.

---

### The Architecture

VolPE operates on a decentralized architecture where each participant runs a **VolPE Worker Application**. The worker applications runs containers for problems assigned to the worker. These containers act as isolated evolutionary ecosystems (islands) that evolve populations locally and periodically communicate with an orchestrator to share genetic material.

* **Orchestrator/Master:** Manages the lifecycle of experiments, synchronizes generations, and handles the migration of high-fitness individuals between nodes.
* **Workers:** Perform the heavy lifting—selection, crossover, and mutation—using high-performance libraries like **DEAP** and **Python Array**.

---

### Key Features

* **Low Overhead:** Built with **gRPC** and **Protobuf** for high-performance, low-latency communication.
* **Memory Efficient:** Uses the native Python `array` module and `struct` serialization to minimize the memory footprint on volunteer machines.
* **Adaptive Evolution:** Supports dynamic noise and diversity coefficients that adjust based on the convergence rate of the local population.
* **Agnostic Design:** While optimized for problems like the **Traveling Salesperson Problem (TSP)**, the platform is designed to handle any optimization task that can be represented as a bitstring, permutation, or real-valued vector.

---

### Technical Stack

* **Core Logic:** [DEAP](https://deap.readthedocs.io/) (Distributed Evolutionary Algorithms in Python)
* **Communication:** gRPC / Protocol Buffers
* **Data Handling:** Python `array` and `struct` for binary-level efficiency
* **Problem Format:** Support for standard `tsplib95` benchmarks

---

### ### Getting Started for Volunteers

1. **Clone the Repository:**
```bash
git clone https://github.com/VolPE-Org/volpe-container.git

```


2. **Install Dependencies:**
```bash
pip install grpcio deap tsplib95

```


3. **Run the Container:**
By default, the container listens on port `8081`.
```bash
python volpe_container.py

```



Once your container is running, it will wait for the **VolPE Orchestrator** to assign a seed population and start the evolutionary process.

---

### ### Contributing

We are always looking for contributors to help optimize the migration protocols and expand the library of supported evolutionary operators. If you are interested in distributed systems or genetic algorithms, feel free to submit a PR or join our community discussions.

**Would you like me to add a section specifically explaining how the `MuPlusLambda` strategy is utilized within the distributed migration logic?**