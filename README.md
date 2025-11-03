
# 🎮 Hackman — Hybrid HMM + DQN Hangman Solver

> UE23CS352A — Machine Learning Hackathon  
> **PES University | Team 7|B Section**

## 👥 Team Members

| Name | SRN |
|---|---|
| Namratha A | PES1UG23AM911 |
| Dhatri P Sriram | PES1UG23AM098 |
| Deepthi M | PES1UG23AM092 |
| Samruddhi Rao | PES1UG23AM915 |

---

This project develops an intelligent Hangman-playing agent using a **Hidden Markov Model (HMM)** for probabilistic language modeling and a **Deep Q-Network (DQN)** for reinforcement-based decision-making.

The aim is to maximize win rate while reducing wrong and repeated guesses, under the constraint of using only the provided 50,000-word corpus.

---

## 🎯 Objective

The agent must guess hidden letters efficiently using machine learning.

**Hackathon Scoring Formula**
```
Final Score = (Success Rate × 2000) - (Wrong Guesses × 5) - (Repeated Guesses × 2)
```

**Key Goals**
- ✅ Maximize success rate
- ❌ Minimize wrong guesses
- ♻️ Avoid repeated guesses

---

## Prerequisites ##

- torch
- numpy
- pandas
- scikit-learn
- matplotlib
- seaborn
- tqdm
- hmmlearn

---

## 🧠 System Architecture

### **Pipeline**
```
Corpus → HMM Training → Letter Probability Estimation
         ↓
Hangman Environment ↔ DQN Agent (Training)
         ↓
Evaluation & Score
```

### **State Representation**
- Masked word encoding
- Guessed letter vector (binary)
- Remaining lives
- HMM probability vector

### **Rewards**
| Action | Reward |
|---|---|
Correct guess | +2.0  
Wrong guess | -1.5  
Repeated guess | -2.0  
Win | +20.0  
Lose | -15.0  

### **Exploration Strategy**
- ε-greedy with exponential decay (1.0 → 0.05)

---

## ⚙️ Hyperparameters

| Parameter | Value |
|---|---|
Episodes | 50,000  
Learning Rate | 0.0001  
Batch Size | 128  
Replay Buffer Size | 500,000  
Discount Factor (γ) | 0.99  
Target Network Update Frequency | Every 500 steps  
Network Architecture | 256 → 256 → 128 (FC layers)  
Optimizer | Adam  
Update Every | 4 steps  
ε-Start | 1.0  
ε-Decay | 0.9995  
ε-Min | 0.05  
HMM Weight | 0.4  
RL Weight | 0.6  

---

## 📊 Evaluation Metrics

- ✅ Success Rate
- ❌ Avg wrong guesses/game
- 🔁 Avg repeated guesses/game
- 🧮 Final hackathon score
- 📈 Reward convergence graph

---

## 🧪 Evaluation Results

| Metric | Value |
|---|---|
Total Words Tested | 2000  
Correctly Guessed | 362  
Success Rate | 18.1%  
Total Score | −8030  
Average Score | −4.015 / game  

---

## 🚀 Key Results

- Stable convergence observed
- Strong improvement vs frequency-based guesser
- Hybrid HMM + DQN outperformed naive RL

---

## 🔮 Future Scope

- Transformer-based masked token predictor
- Curriculum RL (short → long words)
- Multi-agent ensemble voting
- Advanced reward shaping tuning

---

## 📜 License

Developed for **PES University — UE23CS352A ML Hackathon**  
🧠 Academic Use Only

---

