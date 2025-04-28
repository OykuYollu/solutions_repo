# Problem 1

# Orbital Period and Orbital Radius

---

## Motivation

"Kepler's Third Law" links the square of the orbital period with the cube of the orbital radius, forming a cornerstone of celestial mechanics.

- **Purpose:** Understand planetary motions and gravitational interactions from satellites to cosmic scales.
- **Goal:** Connect fundamental principles of gravity to real-world phenomena like satellite orbits and planetary systems.

---

## Derivation of Kepler’s Third Law

Starting from Newton's Law of Universal Gravitation:

$$
F_{gravity} = \frac{GMm}{r^2}
$$

and the centripetal force required for circular motion:

$$
F_{centripetal} = \frac{mv^2}{r}
$$

Equating the two forces:

$$
\frac{GMm}{r^2} = \frac{mv^2}{r}
$$

Simplifying:

$$
v^2 = \frac{GM}{r}
$$

The orbital period \(T\) is related to \(v\) as:

$$
v = \frac{2\pi r}{T}
$$

Substituting:

$$
\left( \frac{2\pi r}{T} \right)^2 = \frac{GM}{r}
$$

Expanding:

$$
\frac{4\pi^2 r^2}{T^2} = \frac{GM}{r}
$$

Cross-multiplying:

$$
4\pi^2 r^3 = GMT^2
$$

Finally, solving for \(T^2\):

$$
T^2 = \frac{4\pi^2}{GM} r^3
$$

For elliptical orbits, replace \(r\) with \(a\) (semi-major axis):

$$
T^2 = \frac{4\pi^2}{GM} a^3
$$

---

## Task List

1. Derive the relationship between the square of the orbital period and the cube of the orbital radius for circular orbits.
2. Discuss the implications of this relationship for astronomy, including its role in calculating planetary masses and distances.
3. Analyze real-world examples, such as the Moon’s orbit around Earth or the orbits of planets in the Solar System.
4. Implement a computational model to simulate circular orbits and verify the relationship.

---

## Deliverables

- A Markdown document containing explanations and Python code.
- A detailed explanation of orbital mechanics and Kepler’s Third Law.
- Graphical representations generated from simulations and real data.
- A discussion on how this relationship extends to elliptical orbits and other celestial bodies.

---

# Graphs Section

## Graph 1: Kepler's Third Law (T² vs r³)

```python
import numpy as np
import matplotlib.pyplot as plt

# Constants
G = 6.67430e-11
M = 1.989e30

radii = np.linspace(5e10, 1e12, 100)
periods = 2 * np.pi * np.sqrt(radii**3 / (G * M))

plt.figure(figsize=(8,6))
plt.plot(radii**3, periods**2, 'o')
plt.xlabel('Orbital Radius Cubed (r³) [m³]')
plt.ylabel('Orbital Period Squared (T²) [s²]')
plt.title("Kepler's Third Law: T² vs r³")
plt.grid(True)
plt.tight_layout()
plt.savefig('kepler_third_law_graph.png')
plt.show()
```

![Kepler's Third Law Graph](kepler_third_law_graph.png)

## Graph 2: Orbital Radius vs Orbital Period

```python
plt.figure(figsize=(8,6))
plt.plot(radii, periods, 'o')
plt.xlabel('Orbital Radius (r) [m]')
plt.ylabel('Orbital Period (T) [s]')
plt.title('Orbital Radius vs Orbital Period')
plt.grid(True)
plt.tight_layout()
plt.savefig('orbital_radius_vs_period.png')
plt.show()
```

![Orbital Radius vs Orbital Period](orbital_radius_vs_period.png)

## Graph 3: Log-Log Plot

```python
plt.figure(figsize=(8,6))
plt.plot(np.log(radii), np.log(periods), 'o')
plt.xlabel('log(Orbital Radius) [log(m)]')
plt.ylabel('log(Orbital Period) [log(s)]')
plt.title('Log-Log Plot: log(T) vs log(r)')
plt.grid(True)
plt.tight_layout()
plt.savefig('log_log_plot.png')
plt.show()
```

![Log-Log Plot: log(T) vs log(r)](log_log_plot.png)

## Graph 4: Orbital Velocity vs Orbital Radius

```python
velocities = np.sqrt(G * M / radii)

plt.figure(figsize=(8,6))
plt.plot(radii, velocities, 'o')
plt.xlabel('Orbital Radius (r) [m]')
plt.ylabel('Orbital Velocity (v) [m/s]')
plt.title('Orbital Velocity vs Orbital Radius')
plt.grid(True)
plt.tight_layout()
plt.savefig('velocity_vs_radius.png')
plt.show()
```

![Orbital Velocity vs Orbital Radius](velocity_vs_radius.png)

## Graph 5: Escape Velocity vs Orbital Radius

```python
import numpy as np
import matplotlib.pyplot as plt

# Constants
G = 6.67430e-11  # m^3 kg^-1 s^-2
M = 1.989e30     # kg

radii = np.linspace(5e10, 1e12, 100)

escape_velocities = np.sqrt(2 * G * M / radii)

plt.figure(figsize=(8,6))
plt.plot(radii, escape_velocities, 'o')
plt.xlabel('Orbital Radius (r) [m]')
plt.ylabel('Escape Velocity (vₑ) [m/s]')
plt.title('Escape Velocity vs Orbital Radius')
plt.grid(True)
plt.tight_layout()
plt.savefig('escape_velocity_vs_radius.png')
plt.show()
```
![Escape Velocity vs Orbital Radius](escape_velocity_vs_radius.png)

## Graph 6: Total Orbital Energy vs Orbital Radius

```python
import numpy as np
import matplotlib.pyplot as plt

# Constants
G = 6.67430e-11  # m^3 kg^-1 s^-2
M = 1.989e30     # kg
m = 5.972e24     # Mass of Earth (kg) -- örnek için

radii = np.linspace(5e10, 1e12, 100)

energies = - (G * M * m) / (2 * radii)

plt.figure(figsize=(8,6))
plt.plot(radii, energies, 'o')
plt.xlabel('Orbital Radius (r) [m]')
plt.ylabel('Total Orbital Energy (E) [J]')
plt.title('Total Orbital Energy vs Orbital Radius')
plt.grid(True)
plt.tight_layout()
plt.savefig('total_orbital_energy_vs_radius.png')
plt.show()
```
![Total Orbital Energy vs Orbital Radius](total_orbital_energy_vs_radius.png)

## Graph 7: T² vs r³ for Real Planets

```python
radii = np.array([5.79e10, 1.082e11, 1.496e11, 2.279e11])
periods = np.array([7.6e6, 1.94e7, 3.15e7, 5.94e7])

plt.figure(figsize=(8,6))
plt.plot(radii**3, periods**2, 'o-', label='Planets: Mercury, Venus, Earth, Mars')
plt.xlabel('Orbital Radius Cubed (r³) [m³]')
plt.ylabel('Orbital Period Squared (T²) [s²]')
plt.title('T² vs r³ for Real Planets')
plt.grid(True)
plt.legend()
plt.tight_layout()
plt.savefig('planets_kepler_law.png')
plt.show()
```

![T² vs r³ for Real Planets](planets_kepler_law.png)

## Planetary Orbital Data Table

| Planet  | Orbital Radius (r) [m] | Orbital Period (T) [s] |
|:-------:|:----------------------:|:----------------------:|
| Mercury | 5.79 × 10¹⁰             | 7.6 × 10⁶              |
| Venus   | 1.082 × 10¹¹            | 1.94 × 10⁷             |
| Earth   | 1.496 × 10¹¹            | 3.15 × 10⁷             |
| Mars    | 2.279 × 10¹¹            | 5.94 × 10⁷             |

## Graph 8: T² vs r³ with Planet Names

```python
import numpy as np
import matplotlib.pyplot as plt

# Planetary Data
radii = np.array([5.79e10, 1.082e11, 1.496e11, 2.279e11])
periods = np.array([7.6e6, 1.94e7, 3.15e7, 5.94e7])
planets = ['Mercury', 'Venus', 'Earth', 'Mars']

plt.figure(figsize=(8,6))
plt.plot(radii**3, periods**2, 'o', markersize=8, label='Planets')

for i in range(len(planets)):
    plt.annotate(planets[i],
                 (radii[i]**3, periods[i]**2),
                 textcoords="offset points",
                 xytext=(0,10),
                 ha='center')

plt.xlabel('Orbital Radius Cubed (r³) [m³]')
plt.ylabel('Orbital Period Squared (T²) [s²]')
plt.title("T² vs r³: Real Planets with Labels")
plt.grid(True)
plt.legend()
plt.tight_layout()
plt.savefig('planets_kepler_law_annotated.png')
plt.show()
```
![T² vs r³: Real Planets with Labels](planets_kepler_law_annotated.png)

# Conclusion

In this project, we derived Kepler's Third Law starting from Newton's principles and verified it using simulated and real-world planetary data. Various graphical analyses confirmed the proportional relationship between the square of the orbital period and the cube of the orbital radius. This study enhances our understanding of orbital mechanics, an essential aspect of celestial physics.

[visit my colab](https://colab.research.google.com/drive/1mf6_KAMZWRRb9Eo6LtPy0lwP0k8U7Gyy?usp=sharing)