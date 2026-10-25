# AI Adaptive Traffic Signal Control (Q-Learning Simulation)

An interactive browser simulation that compares a **fixed-timer traffic signal** with an **AI controller trained using Q-learning**, a reinforcement learning algorithm. Both controllers face the same random traffic, so the comparison is fair.

**Live demo:** https://[your-username].github.io/traffic-ai-simulation/

## Features
- Side-by-side intersections: fixed timer vs AI
- Live metrics: queue length, average waiting time, vehicles served
- Percentage improvement shown in real time
- Sliders to change North–South and East–West traffic
- Pause, reset, speed control, and an option to train the AI further

## How it works
| Element | Definition |
|---|---|
| Agent | Traffic signal controller |
| State | North–South queue level, East–West queue level, current phase, minimum-green flag (400 states) |
| Actions | Keep the current phase or switch |
| Reward | Negative total queue length, minus a small penalty for switching |

Update rule: `Q(s,a) ← Q(s,a) + α [ r + γ max Q(s′,a′) − Q(s,a) ]`
with α = 0.1 and γ = 0.9. The agent explores with an ε-greedy policy.

## Results
Tested over 5,000 ticks per scenario, averaged over 10 random seeds:

| NS rate | EW rate | Fixed timer wait (s) | AI wait (s) | Improvement |
|---|---|---|---|---|
| 0.20 | 0.20 | 12.4 | 9.1 | 26.5% |
| 0.30 | 0.10 | 13.8 | 7.9 | 43.2% |
| 0.35 | 0.05 | 17.9 | 6.2 | 65.6% |
| 0.40 | 0.15 | 43.7 | 9.9 | 77.2% |
| 0.10 | 0.30 | 13.9 | 7.9 | 43.4% |
| 0.30 | 0.30 | 14.8 | 12.5 | 15.7% |

## Run locally
Download `index.html` and open it in any web browser. No installation is needed.

## Limitations
- A single intersection with two phases
- No pedestrians, turning lanes or emergency vehicles
- Tabular Q-learning does not scale to large road networks

## Technologies
HTML5, CSS, JavaScript (canvas). No external libraries.

## Author
Madhav Kishore K S 24BDS0359
Subject: Artificial Intelligence, Case Study (2026)
