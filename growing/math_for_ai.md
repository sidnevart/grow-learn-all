# Математика для AI / ML / Physical AI

> **Цель:** Формальная математическая база для AI/ML, робототехники, autonomous systems
> **Время:** 4-6 месяцев
> **Формат:** Теория + Python/JAX практика + применение к твоим проектам

---

## Зачем тебе математика

Ты умеешь **строить** AI-системы (RAG, agents, code review bot). Но не хватает **понимания почему** они работают:
- Почему transformer attention именно такая формула?
- Почему gradient descent сходится?
- Как оптимизировать latency AI inference?
- Как робот "видит" пространство?

Это нужно для:
- **Top AI research/engineering роли** (OpenAI, Anthropic, DeepMind)
- **Physical AI / Robotics** (Tesla Optimus, Figure AI, Boston Dynamics)
- **MS/PhD в AI** (MIT, Stanford, CMU)
- **AI Infrastructure** (оптимизация inference, quantization)

---

## Что именно учить

### 1. Linear Algebra (неделя 1-4)

**Темы:**
- Vectors, matrices, tensors
- Matrix operations (multiplication, transpose, inverse)
- Eigenvalues, eigenvectors
- SVD (Singular Value Decomposition)
- Linear transformations
- Vector spaces, subspaces, basis
- Norms (L1, L2, Frobenius)
- PCA (Principal Component Analysis)

**Ресурсы:**

| Ресурс | Тип | Время | Ссылка |
|--------|-----|-------|--------|
| MIT 18.06 Linear Algebra | Курс (Gilbert Strang) | 35 лекций | [ocw.mit.edu/18-06](https://ocw.mit.edu/courses/18-06-linear-algebra-spring-2010/) |
| 3Blue1Brown — Essence of Linear Algebra | YouTube | 3 часа | [youtube.com/playlist](https://www.youtube.com/playlist?list=PLZHQObOWTQDPD3MizzM2xVFitgF8hE_ab) |
| Introduction to Linear Algebra (Strang) | Книга | 20 часов | [Amazon](https://amazon.com) |
| Khan Academy — Linear Algebra | Интерактив | 15 часов | [khanacademy.org/math/linear-algebra](https://www.khanacademy.org/math/linear-algebra) |

**Практика:**
- Реализовать matrix multiplication на Python + NumPy
- PCA на датасете (руками, не sklearn)
- SVD для image compression

**Output:** Пост: "Linear Algebra для AI: что реально используется в production"

### 2. Calculus (неделя 5-6)

**Темы:**
- Derivatives, partial derivatives
- Chain rule (backpropagation foundation)
- Gradients, Jacobian, Hessian
- Optimization basics (minima, maxima)
- Integrals (basic)

**Ресурсы:**

| Ресурс | Тип | Время | Ссылка |
|--------|-----|-------|--------|
| MIT 18.01 Single Variable Calculus | Курс | 20 лекций | [ocw.mit.edu/18-01](https://ocw.mit.edu/courses/18-01-single-variable-calculus-fall-2006/) |
| MIT 18.02 Multivariable Calculus | Курс | 20 лекций | [ocw.mit.edu/18-02](https://ocw.mit.edu/courses/18-02-multivariable-calculus-fall-2007/) |
| 3Blue1Brown — Essence of Calculus | YouTube | 2 часа | [youtube.com/playlist](https://www.youtube.com/playlist?list=PLZHQObOWTQDMsr9K-rj53DwVRMYO3t5Yr) |
| Khan Academy — Calculus | Интерактив | 20 часов | [khanacademy.org/math/calculus-1](https://www.khanacademy.org/math/calculus-1) |

**Практика:**
- Реализовать gradient descent с нуля (на Python)
- Backpropagation для simple neural network (руками)

**Output:** Пост: "Backpropagation с нуля: почему chain rule работает"

### 3. Probability & Statistics (неделя 7-10)

**Темы:**
- Probability distributions (normal, binomial, Poisson)
- Bayes' Theorem
- Random variables, expectation, variance
- Covariance, correlation
- Maximum Likelihood Estimation (MLE)
- Central Limit Theorem
- Hypothesis testing
- Information Theory (entropy, KL divergence)

**Ресурсы:**

| Ресурс | Тип | Время | Ссылка |
|--------|-----|-------|--------|
| MIT 6.041 Probabilistic Systems | Курс | 25 лекций | [ocw.mit.edu/6-041](https://ocw.mit.edu/courses/6-041-probabilistic-systems-analysis-and-applied-probability-fall-2010/) |
| Harvard Statistics 110 | Курс (Joe Blitzstein) | 35 лекций | [youtube.com/playlist](https://www.youtube.com/playlist?list=PL2SOU6wwxBG3mzdtYz_4N5D2W11uHjNPb) |
| 3Blue1Bayesian | YouTube | 2 часа | [youtube.com](https://www.youtube.com) |
| Khan Academy — Statistics | Интерактив | 15 часов | [khanacademy.org/math/statistics-probability](https://www.khanacademy.org/math/statistics-probability) |

**Практика:**
- Naive Bayes classifier с нуля
- Bayesian update для recommendation system
- A/B testing framework (power analysis)

**Output:** Пост: "Bayesian Thinking для инженера: от интуиции к формуле"

### 4. Optimization (неделя 11-12)

**Темы:**
- Gradient Descent (batch, stochastic, mini-batch)
- Momentum, AdaGrad, Adam
- Convex optimization basics
- Lagrange multipliers
- Linear Programming (basics)

**Ресурсы:**

| Ресурс | Тип | Время | Ссылка |
|--------|-----|-------|--------|
| Stanford CS229 (Andrew Ng) | Курс | 20 лекций | [cs229.stanford.edu](https://cs229.stanford.edu) |
| Convex Optimization (Boyd) | Книга | 20 часов | [web.stanford.edu/~boyd/cvxbook](https://web.stanford.edu/~boyd/cvxbook/) — **бесплатно** |
| fast.ai — Practical Deep Learning | Курс | 30 часов | [course.fast.ai](https://course.fast.ai) |
| MIT 6.036 Introduction to Machine Learning | Курс | 15 лекций | [ocw.mit.edu/6-036](https://ocw.mit.edu/courses/6-036-introduction-to-machine-learning-fall-2020/) |

**Практика:**
- Реализовать Adam optimizer с нуля
- Optimize hyperparameters для твоего RAG pipeline

**Output:** Пост: "Adam vs SGD: когда что использовать в production AI"

### 5. Machine Learning (неделя 13-16)

**Темы:**
- Supervised learning (regression, classification)
- Unsupervised learning (clustering, dimensionality reduction)
- Neural Networks (feedforward, CNN, RNN basics)
- Transformers (attention mechanism, BERT, GPT)
- RAG (Retrieval-Augmented Generation)
- LLM fine-tuning basics

**Ресурсы:**

| Ресурс | Тип | Время | Ссылка |
|--------|-----|-------|--------|
| fast.ai — Practical Deep Learning | Курс | 30 часов | [course.fast.ai](https://course.fast.ai) |
| Stanford CS229 | Курс | 20 лекций | [cs229.stanford.edu](https://cs229.stanford.edu) |
| Stanford CS224N (NLP) | Курс | 20 лекций | [web.stanford.edu/class/cs224n](https://web.stanford.edu/class/cs224n/) |
| Andrej Karpathy — Neural Networks: Zero to Hero | YouTube | 10 часов | [youtube.com/playlist](https://www.youtube.com/playlist?list=PLAqhIrjkxbuWI23v9cThsA9GvCAUh9JxF) |
| Hugging Face NLP Course | Интерактив | 10 часов | [huggingface.co/learn/nlp-course](https://huggingface.co/learn/nlp-course) |
| Papers We Love — Attention Is All You Need | Paper | 2 часа | [arxiv.org/abs/1706.03762](https://arxiv.org/abs/1706.03762) |

**Практика:**
- Fine-tune BERT для классификации (Hugging Face)
- Implement transformer attention from scratch (PyTorch/JAX)
- Build RAG pipeline with vector DB (pgvector, Weaviate)

**Output:** Пост: "RAG pipeline с нуля: embeddings, retrieval, generation"

### 6. Physical AI / Robotics (неделя 17-20, optional)

Если цель — Physical AI (Tesla Optimus, Figure AI, Boston Dynamics):

**Темы:**
- Kinematics, Dynamics
- Control theory (PID, MPC)
- SLAM (Simultaneous Localization and Mapping)
- Computer Vision basics (CNN для object detection)
- Reinforcement Learning basics
- Sim-to-real transfer

**Ресурсы:**

| Ресурс | Тип | Время | Ссылка |
|--------|-----|-------|--------|
| CS285 (Berkeley) — Deep RL | Курс | 20 лекций | [rail.eecs.berkeley.edu/deeprlcourse](http://rail.eecs.berkeley.edu/deeprlcourse/) |
| Stanford CS231n (Computer Vision) | Курс | 16 лекций | [cs231n.stanford.edu](https://cs231n.stanford.edu) |
| Modern Robotics (Northwestern) | Курс | 10 часов | [modernrobotics.northwestern.edu](https://modernrobotics.northwestern.edu) |
| MuJoCo Tutorial | Tutorial | 5 часов | [mujoco.org](https://mujoco.org) |
| PyBullet / Isaac Sim | Симулятор | 5 часов | [pybullet.org](https://pybullet.org) |

**Практика:**
- Train RL agent in MuJoCo / Isaac Sim
- Object detection with YOLO
- Simple SLAM implementation

**Output:** Пост: "От backend к робототехнике: мой путь к Physical AI"

---

## Книги

| Книга | Автор | Тема | Где |
|-------|-------|------|-----|
| Introduction to Linear Algebra | Gilbert Strang | Linear Algebra | [Amazon](https://amazon.com) |
| Convex Optimization | Boyd & Vandenberghe | Optimization | [Бесплатно](https://web.stanford.edu/~boyd/cvxbook/) |
| Pattern Recognition and Machine Learning | Bishop | ML Theory | [Amazon](https://amazon.com) |
| Deep Learning (Goodfellow) | Goodfellow et al. | Deep Learning | [Amazon](https://amazon.com) / [Бесплатно](https://www.deeplearningbook.org) |
| Mathematics for Machine Learning | Deisenroth et al. | All math for ML | [Бесплатно](https://mml-book.github.io/book/mml-book.pdf) |
| Reinforcement Learning: An Introduction | Sutton & Barto | RL | [Бесплатно](http://incompleteideas.net/book/the-book-2nd.html) |
| Probabilistic Robotics | Thrun et al. | Robotics | [Amazon](https://amazon.com) |

---

## Технологический стек для практики

| Tool | Для чего | Ссылка |
|------|----------|--------|
| Python + NumPy | Linear algebra | [numpy.org](https://numpy.org) |
| Python + SciPy | Optimization, stats | [scipy.org](https://scipy.org) |
| PyTorch | Deep learning | [pytorch.org](https://pytorch.org) |
| JAX | High-performance ML | [github.com/google/jax](https://github.com/google/jax) |
| Hugging Face Transformers | NLP, LLMs | [huggingface.co](https://huggingface.co) |
| LangChain | RAG, agents | [langchain.com](https://langchain.com) |
| pgvector | Vector DB | [github.com/pgvector/pgvector](https://github.com/pgvector/pgvector) |
| MuJoCo / Isaac Sim | Robotics sim | [mujoco.org](https://mujoco.org) |
| OpenCV | Computer vision | [opencv.org](https://opencv.org) |
| Weights & Biases | Experiment tracking | [wandb.ai](https://wandb.ai) |

---

## Трекер: 20-недельный план

| Неделя | Фокус | Output |
|--------|-------|--------|
| 1 | Vectors, matrices, operations | NumPy практика |
| 2 | Matrix decomposition, SVD | Image compression project |
| 3 | Eigenvalues, eigenvectors | PCA на датасете |
| 4 | Linear transformations, vector spaces | Пост: "LA для AI" |
| 5 | Derivatives, chain rule | Gradient descent с нуля |
| 6 | Partial derivatives, backprop | Backprop from scratch |
| 7 | Distributions, Bayes | Naive Bayes classifier |
| 8 | Random variables, MLE | Пост: "Bayesian thinking" |
| 9 | Information theory | Entropy в NLP |
| 10 | Hypothesis testing | A/B testing framework |
| 11 | Gradient descent advanced | Adam from scratch |
| 12 | Convex optimization | Пост: "Optimization в production" |
| 13 | Supervised learning | Linear/logistic regression |
| 14 | Neural networks | Simple NN in PyTorch |
| 15 | CNN, RNN | Image classifier |
| 16 | Transformers, RAG | RAG pipeline |
| 17 | RL basics | Cartpole in MuJoCo |
| 18 | Computer vision basics | Object detection |
| 19 | Sim-to-real | Robot simulation |
| 20 | Review, arXiv paper draft | Paper draft |

---

**Последнее обновление:** 16 May 2026
