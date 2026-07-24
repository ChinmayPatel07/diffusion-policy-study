# 🤖 Exploring Diffusion Policy and RL for Robot Learning

*Status: In Progress · Penn State University Park · CS Undergraduate · MIT License*

> *Can we teach robots to handle uncertainty the same way diffusion models handle noise?*  
> This repo documents my personal study of **Diffusion Policy** and its combination with **Reinforcement Learning**.

---

## 📌 Overview

This is a personal learning repository focused on deeply understanding **Diffusion Policy** — one of the most influential recent advances in robot learning — and how **Reinforcement Learning** can push it beyond what demonstrations alone can achieve.

Standard robot policies (e.g. Gaussian policies) collapse when faced with tasks that have multiple valid solutions. Diffusion Policy solves this by representing actions as the output of an iterative denoising process — naturally capturing complex, multimodal action distributions.

This study goes further: exploring how RL fine-tuning methods (DDPO, DPPO) allow a pretrained diffusion policy to improve through environment interaction, optimizing directly for task reward rather than just copying demonstrations.

---

## 📚 Papers

| Paper | Authors | Venue | Link |
|---|---|---|---|
| **Diffusion Policy** — *Visuomotor Policy Learning via Action Diffusion* | Chi et al. | RSS 2023 / IJRR 2024 | [arXiv](https://arxiv.org/abs/2303.04137) |
| **DDPO** — *Training Diffusion Models with Reinforcement Learning* | Black et al. | ICLR 2024 | [arXiv](https://arxiv.org/abs/2305.13301) |
| **DPPO** — *Diffusion Policy Policy Optimization* | Ren et al. | ICLR 2025 | [arXiv](https://arxiv.org/abs/2409.00588) |

---

## 🧠 Key Concepts

### Why Diffusion Policy?

Standard policies predict a single action or a unimodal Gaussian distribution. When a task has multiple valid strategies — e.g. grasping an object from the left *or* right — a Gaussian policy averages them into an invalid middle action.

Diffusion Policy generates actions through an iterative denoising process: starting from random noise and refining it step-by-step into a precise action, conditioned on the robot's current observation. This naturally handles **multimodal action distributions**.

### Why RL on top?

Diffusion Policy trained via imitation learning is bounded by the quality of demonstrations. RL fine-tuning allows the policy to explore and improve *beyond* what any demonstration showed — optimizing directly for task reward.

| Method | Core Idea | Strength |
|---|---|---|
| **DDPO** | Treat each denoising step as an RL action (single MDP) | Clean formulation, strong for image generation tasks |
| **DPPO** | Two-layer MDP (environment + denoising) + PPO | State-of-the-art for robot manipulation fine-tuning |

---

## 🗂️ Repository Structure

```
diffusion-policy-study/
│
├── notes/
│   ├── 01-diffusion-policy.md           # Paper summary + key concepts
│   ├── 02-ddpo.md                       # DDPO: MDP framing of denoising
│   ├── 03-dppo.md                       # DPPO: two-layer MDP + PPO
│   └── concepts/
│       ├── rl-basics.md                 # RL fundamentals
│       ├── diffusion-models.md          # How diffusion works
│       └── multimodal-actions.md        # Why Gaussian policies fail
│
├── notebooks/
│   ├── 01-pusht-inference.ipynb         # Running pretrained model on PushT
│   ├── 02-denoising-visualization.ipynb # Visualizing the denoising chain
│   └── 03-ablations.ipynb              # Experimenting with hyperparameters
│
├── results/
│   ├── figures/                         # Plots and diagrams
│   └── videos/                          # Robot task rollouts
│
└── README.md
```

---

## 🔗 Resources

- [Official Diffusion Policy Repo](https://github.com/real-stanford/diffusion_policy)
- [Diffusion Policy Project Website](https://diffusion-policy.cs.columbia.edu/)
- [DDPO Paper](https://arxiv.org/abs/2305.13301)
- [DPPO Paper](https://arxiv.org/abs/2409.00588)

---

## 👤 About

**Chinmay Patel** — Computer Science undergraduate at Penn State University Park  
Interests: Robot learning, generative models, reinforcement learning  
GitHub: [@ChinmayPatel07](https://github.com/ChinmayPatel07)

---

*Started July 2026 · Penn State University Park*
