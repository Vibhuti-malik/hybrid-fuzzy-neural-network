# Introduction to Intelligent Systems - Assignment



## Q2 — Hybrid Intelligent System: Student Performance Prediction

### 

### Problem Statement

Develop a **hybrid intelligent system** combining fuzzy logic and a neural network to predict student performance level as **Poor**, **Average**, or **Good**.

### 

### Inputs \& Output

|Variable|Type|Range (in %)|
|-|-|-|
|Attendance|Input|0 – 100|
|Assignment Marks|Input|0 – 100|
|Test Marks|Input|0 – 100|
|Performance Level|Output|Poor / Average / Good|

### 

### System Architecture



\[Attendance]        ┐
\[Assignment Marks]  ├──► FUZZY LAYER ──► \[Fuzzy Score (0–100)]
\[Test Marks]        ┘                             │

▼

┌─────────────────────────────────┐
│         NEURAL NETWORK          │
│  Input(4) → Dense(16) →         │
│  Dense(8) → Softmax(3)          │
└─────────────────────────────────┘
│
▼
\[Poor / Average / Good]



### How Fuzzy Logic and Neural Network are Integrated

**Fuzzy Layer — Handles Linguistic Uncertainty**

* Converts numeric inputs into fuzzy membership degrees

  * e.g., Attendance = 72% → 40% *medium*, 60% *high*
* Applies IF-THEN rules to compute a fuzzy performance score
* Mimics how a teacher intuitively evaluates a student

**Neural Network Layer — Learns from Data**

* Takes all 3 original inputs **plus** the fuzzy score as 4 features
* Learns non-linear patterns that fuzzy rules may miss
* Uses backpropagation to automatically tune its weights



||Fuzzy Logic|Neural Network|
|-|-|-|
|Strength|Interpretable rules, handles vagueness|Learns complex patterns from data|
|Weakness|Rules must be defined manually|Needs labeled training data|
|Role in Hybrid|Pre-processes inputs linguistically|Final classification decision|

### 

### Fuzzy Rules Used (8 Rules)

|Attendance|Assignment Marks|Test Marks|Performance|
|-|-|-|-|
|High|High|High|Good|
|High|Medium|High|Good|
|Medium|Medium|Medium|Average|
|Medium|High|Medium|Average|
|Low|Low|Low|Poor|
|Low|Medium|Low|Poor|
|High|Low|Medium|Average|
|Medium|Low|Low|Poor|

### 

### Neural Network Architecture

Input Layer    →  4 neurons  (Attendance, Assignment, Test, Fuzzy Score)
Hidden Layer 1 → 16 neurons  (ReLU activation)
Hidden Layer 2 →  8 neurons  (ReLU activation)
Output Layer   →  3 neurons  (Softmax → Poor, Average, Good)

* **Optimizer:** Adam
* **Loss Function:** Categorical Cross-Entropy
* **Epochs:** 100

### 

### How to Run

1. Open [Google Colab](https://colab.research.google.com)
2. Upload `Q2\\\\\\\_Hybrid\\\\\\\_Fuzzy\\\\\\\_NeuralNetwork.ipynb`
3. Click **Runtime → Run All**

### 

### Outputs

* Membership function plots for all 3 inputs
* Live prediction for custom student inputs



## Dependencies

All dependencies are installed automatically inside the notebook using `!pip install`.

|Library|Purpose|
|-|-|
|`scikit-fuzzy`|Fuzzy logic inference system|
|`numpy`|Numerical computation|
|`matplotlib`|Plotting membership functions and graphs|
|`tensorflow / keras`|Neural network|
|`scikit-learn`|Train/test split, evaluation metrics|
|`pandas`|Dataset management|



## Credits

**Developed by: Vibhuti Malik
Course Project:** Introduction to Intelligent Systems
**Institution:** Manipal University Jaipur



## License

This project is open-source for learning and portfolio use. No commercial usage allowed without permission.

