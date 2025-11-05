# 🧬 Genetic Algorithm – Rocket Simulation

## 🚀 Overview
This project is a **genetic algorithm visualization** built with **Python + Pygame + Matplotlib**.  
Each rocket (agent) tries to reach a green **target** at the top of the screen by evolving its movement vectors through generations.

Rockets **evolve over time** — the best performers are selected, crossover occurs, and mutations are introduced.  
Over successive generations, the population learns the optimal path to the target, even when obstacles are present.

---

## 🎮 Features
✅ Fully visualized real-time simulation using **Pygame**  
✅ Live fitness graph updated each generation using **Matplotlib**  
✅ Movable obstacle (drag with mouse to change difficulty dynamically)  
✅ Adjustable parameters for experimentation (mutation rate, lifespan, population size)  
✅ Multithreaded plotting for smooth visualization  

---

## ⚙️ How It Works

### 🧠 Algorithm Logic
The simulation follows the **Genetic Algorithm (GA)** process:

1. **Initialization** – Generate a population of rockets with random DNA (movement vectors).  
2. **Simulation** – Each rocket applies DNA step-by-step as movement forces.  
3. **Evaluation** – Fitness is based on distance to the target.  
   - Completed rockets are rewarded  
   - Crashed rockets are penalized  
4. **Selection** – Parents are chosen according to fitness and crossover occurs.  
5. **Mutation** – Random gene modifications preserve diversity.  
6. **Repeat** – New generation is born and evolves again!  

---

## 🧩 Code Structure & Explanation

### **Rocket Class**
Handles individual rocket behavior:
```python
class Rocket:
    def update(self, step):
        self.apply_force(self.dna[step])
        self.vel += self.acc
        self.pos += self.vel
        self.acc *= 0
        if (target - self.pos).length() < 10:
            self.completed = True
        if obstacle.collidepoint(self.pos.x, self.pos.y):
            self.crashed = True
