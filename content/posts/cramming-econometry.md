+++
date = '2025-11-28T02:52:08+02:00'
draft = false
title = 'Cramming Econometry'
summary = "2hr cramming material from the multiple choise questions and the slide."
+++


This is a **high-intensity, 2-hour cram plan** designed to maximize your score based on the files you provided. Since you have a mix of MCQs and output-based exercises, we will split the time: **60 minutes for Exercises (the heavy lifting)** and **45 minutes for MCQ Concepts**, with **15 minutes for final formula review**.

---

### **PART 1: Mastering the Exercises (60 Minutes)**

**Goal:** Be able to read the regression output and calculate t-stats, F-stats, and predictions immediately.

#### **1\. Interpreting the Coefficients ($\\beta$)**

You must look at the functional form (Logs vs. Linear) to interpret the results correctly.

- **Linear-Linear ($y \= \\beta\_1 \+ \\beta\_2 x$):** A 1 unit increase in $x$ leads to a $\\beta\_2$ unit increase in $y$.
  
- **Log-Log ($\\ln(y) \= \\beta\_1 \+ \\beta\_2 \\ln(x)$):** A **1%** increase in $x$ leads to a **$\\beta\_2$%** increase in $y$ (Elasticity). 1111
  
- **Log-Linear ($\\ln(y) \= \\beta\_1 \+ \\beta\_2 x$):** A 1 unit increase in $x$ leads to a **($100 \\times \\beta\_2$ )%** increase in $y$ (Semi-elasticity). 2222
  
- **Linear-Log ($y \= \\beta\_1 \+ \\beta\_2 \\ln(x)$):** A 1% increase in $x$ leads to a **$(\\beta\_2 / 100)$** unit increase in $y$. 3
  

**Tip:** "Ceteris Paribus" (holding all other variables constant) is the key phrase for Multiple Regression interpretation. 4

#### **2\. Hypothesis Testing (t-tests)**

You will likely be asked to test if a coefficient equals a specific value (usually 0).

- **Null Hypothesis ($H\_0$):** $\\beta\_k \= c$ (usually $c=0$).
  
- **Formula:**  
  $$t \= \\frac{\\text{Estimated Coefficient} \- \\text{Hypothesized Value}}{\\text{Standard Error}} \= \\frac{b\_k \- c}{se(b\_k)}$$  
  5555
  
- **Decision Rule (Large Sample/Normal):**
  
  - If $|t| \> 1.96$, reject $H\_0$ at 5% significance.
  - If $|t| \> 2.58$, reject $H\_0$ at 1% significance.
  - **Shortcut:** Look at the **P-value** column. If $p \< 0.05$, the variable is statistically significant (Reject $H\_0$). 6

#### **3\. Confidence Intervals**

Constructing a 95% confidence interval for a coefficient.

- **Formula:**  
  $$\\text{Coefficient} \\pm (\\text{Critical Value} \\times \\text{Standard Error})$$
- For large samples (95%), use **1.96**.
- **Calculation:** $\[b\_k \- 1.96 \\cdot se(b\_k), \\quad b\_k \+ 1.96 \\cdot se(b\_k)\]$ 7777

#### **4\. The F-Test (Joint Hypotheses)**

Use this when testing if **multiple** coefficients are simultaneously zero (e.g., "Test if $\\beta\_3 \= 0$ AND $\\beta\_4 \= 0$").

- You need two models:
  
  1. **Unrestricted (U):** The full model.
  2. **Restricted (R):** The model *without* the variables you are testing.
- Formula (from Equations.pdf):
  
  $$F \= \\frac{(SSE\_R \- SSE\_U)/J}{SSE\_U/(N-K)}$$  
  888
  
  - $SSE\_R$: Sum of Squared Errors (Restricted).
  - $SSE\_U$: Sum of Squared Errors (Unrestricted).
  - $J$: Number of restrictions (variables removed).
  - $N$: Sample size.
  - $K$: Total number of coefficients in the Unrestricted model (including intercept).

#### **5\. Prediction (Watch out for Logs\!)**

- **Linear Model:** Simply plug the $x$ values into the estimated equation.
  
  - $\\hat{y} \= b\_1 \+ b\_2(x\_{new})$ 9
- **Log-Linear Model ($\\ln(y) \= \\dots$):**
  
  - If calculating the **expected $y$** (not $\\ln y$), you must correct for variance.
    
  - **Corrected Predictor:** $\\hat{y}\_c \= \\exp(\\widehat{\\ln y}) \\times \\exp(\\hat{\\sigma}^2/2)$ 10101010
    
  - *Where $\\hat{\\sigma}$ is the "S.E. of regression" from the output table.*
    

#### **6\. Dummy Variables**

- **Intercept Dummy:** Shifts the line up or down.
  - *Example:* $Wage \= \\beta\_1 \+ \\beta\_2 Male$. Male earns $\\beta\_2$ more than Female.
- **Interaction Dummy ($D \\times x$):** Changes the **slope**.
  - *Example:* $Wage \= \\beta\_1 \+ \\beta\_2 Educ \+ \\beta\_3 (Male \\times Educ)$.
  - Returns to education for Females: $\\beta\_2$.
  - Returns to education for Males: $\\beta\_2 \+ \\beta\_3$. 11111111

---

### **PART 2: MCQ High-Yield Concepts (45 Minutes)**

**Goal:** Recognize keywords for the 8 theory questions.

#### **Simple & Multiple Regression (Ch 2, 5\)**

- **OLS Goal:** Minimizes the **Sum of Squared Residuals (SSE)**. 12
  
- **$R^2$ (Coefficient of Determination):** The proportion of variation in $y$ explained by $x$. 13
  
  - $R^2 \= 1 \- (SSE/SST)$. 14
- **Adjusted $R^2$:** Used to compare models with *different numbers of variables*. It penalizes adding useless variables (unlike regular $R^2$ which never goes down). 15
  
- **Omitted Variable Bias:** If you leave out a relevant variable correlated with $x$, your estimates are **biased**. 16161616
  
- **Multicollinearity:** When $x$ variables are highly correlated.
  
  - *Symptom:* High $R^2$ but **insignificant t-tests** (large standard errors). 17
    
  - *Consequence:* Hard to isolate individual effects, but **prediction is still good**.
    

#### **Hypothesis Testing (Ch 3, 6\)**

- **Type I Error:** Rejecting $H\_0$ when it is actually **True**. (Probability \= $\\alpha$). 18
  
- **Type II Error:** Failing to reject $H\_0$ when it is **False**. 19
  
- **P-value:** The lowest significance level at which you can reject $H\_0$. If p-value \< $\\alpha$, Reject. 20
  
- **Chow Test:** An F-test used to see if regression parameters are different between two groups (structural break). 21
  

#### **Modeling Issues & Diagnostics (Ch 4, 8\)**

- **Heteroskedasticity:** The variance of the error term is **not constant** (it varies with $x$). 22
  
  - *Consequence:* OLS is still unbiased, but standard errors are wrong (t-tests are invalid). 23
    
  - *Detection:* **White Test**, **Breusch-Pagan Test**. 24
    
  - *Fix:* Use **White's Robust Standard Errors** (HC standard errors) or Weighted Least Squares (WLS). 25
    
- **Jarque-Bera Test:** Tests if the error terms are **Normally Distributed**. 26
  
- **RESET Test:** Tests for **functional form misspecification** (e.g., missing squares or interaction terms). 27
  
- **Forecasting Errors:** Large errors occur when the sample size $N$ is small, or the new $x\_0$ is far from the mean $\\bar{x}$. 28
  

---

### **PART 3: Final Check \- The "Cheat Sheet" Strategy (15 Minutes)**

*Open Equations.pdf and locate these specific formulas so you don't panic.*

1. **Find the Variance formulas:** Note that $Var(b\_2)$ has $\\Sigma(x-\\bar{x})^2$ in the denominator. Larger spread in $x$ \= Smaller Variance (Good). 29
  
2. **Find the F-statistic formula:** 30 \- You will likely need the $(SSE\_R \- SSE\_U)$ version.
  
3. **Find the Prediction Interval:** Notice the $+1$ inside the bracket for forecast variance (prediction is uncertain because of the error term $\\epsilon$). 31
  

### **Quick Drill (Self-Test):**

1. **If $P \> |t|$ is 0.0000:** Reject $H\_0$. It is significant.
  
2. **If $P \> |t|$ is 0.35:** Do not reject. Not significant.
  
3. **Positive coefficient on $x^2$:** The curve is U-shaped (convex). 32
  
4. **Dependent variable is $\\ln(y)$:** Remember to interpret coefficients as percentages (approx).
  
## PART 4: Paper in go

{{< details summary="Εκφώνηση Εργασίας" >}}

**Π.Μ.Σ. Λογιστική και Χρηματοοικονομική Ομαδική εργασία στα πλαίσια του μαθήματος Ανάλυση Δεδομένων στη Λογιστική και Χρηματοοικονομική**

**Γενικές πληροφορίες**

- Η ομαδική εργασία εκπονείται από ομάδες φοιτητών μέχρι τρία μέλη το μέγιστο και θα πρέπει να έχει έκταση περίπου 2.500 λέξεις (χωρίς το παράρτημα). Αποκλίσεις \+/- 15% στην έκταση της εργασίας είναι αποδεκτές.
- Μόνο ένα μέλος κάθε ομάδας φοιτητών χρειάζεται να υποβάλει την εργασία στο eclass πριν από την 23η Νοεμβρίου 2025, 23:59μ.μ. Αργοπορημένες υποβολές δεν γίνονται αποδεκτές.
- Η ομαδική εργασία είναι υποχρεωτική και διαμορφώνει σε ποσοστό 25% τον τελικό βαθμό του μαθήματος.
- Για την επιτυχή ολοκλήρωση του μαθήματος χρειάζεται προβιβάσιμος βαθμός στην τελική γραπτή εξέταση (\>=5).
- Ο τελικός βαθμός για το μάθημα υπολογίζεται ως: (75% \* βαθμός γραπτής εξέτασης) \+ (25% \* βαθμός ομαδικής εργασίας).

**Θέμα εργασίας: Εκτίμηση ενός γραμμικού μοντέλου παλινδρόμησης – CAPM**

1. **Χρησιμοποιήστε το αρχείο project data.xlsx** που είναι αναρτημένο στο eclass:
  
  - **A.** Επιλέξετε μηνιαίες τιμές του δείκτη **US Market Index** (φύλλο εργασίας: index) και υπολογίστε τις λογαριθμικές διαφορές για να κατασκευάσετε τις αποδόσεις του δείκτη $R\_M$.
  - **B.** Στη συνέχεια διαλέξτε μία εισηγμένη εταιρεία της επιλογής σας που βρίσκεται στο αρχείο (φύλλο εργασίας: stocks) και υπολογίστε τις λογαριθμικές διαφορές για να κατασκευάσετε τις αποδόσεις της μετοχής $R\_i$.
  - **C.** Επιλέξετε τις μηνιαίες τιμές για το χωρίς κίνδυνο επιτόκιο (**risk-free rate, $R\_f$**) ως το **U.S. Treasury bill 3-month** (φύλλο εργασίας: risk free). Διαιρέστε το ετησιοποιημένο επιτόκιο που κατεβάσατε με το 12 για να υπολογίσετε το μηνιαίο επιτόκιο χωρίς κίνδυνο.
  - **D.** Κρατήστε τα ιστορικά δεδομένα μόνο για τη κοινή περίοδο που είναι διαθέσιμα και για τις τρεις μεταβλητές που κατεβάσατε, δηλαδή (i) δείκτη, (ii) μετοχής, (iii) επιτοκίου χωρίς κίνδυνο.
2. **Υπολογίστε τις υπερβάλλουσες αποδόσεις** της μετοχής και του δείκτη ως $ER\_{i,t} \= R\_{i,t} \- R\_{f,t-1}$ και $ER\_{M,t} \= R\_{M,t} \- R\_{f,t-1}$. Παρατηρήστε ότι το επιτόκιο χωρίς κίνδυνο αναφέρεται στην προηγούμενη περίοδο (t-1) από αυτή των αποδόσεων του δείκτη και της μετοχής (t).
  
3. **Εκτιμήστε το Υπόδειγμα Αποτίμησης Κεφαλαιακών Περιουσιακών Στοιχείων (Capital Asset Pricing Model, CAPM)** σύμφωνα με την παρακάτω εξίσωση παλινδρόμησης (όπου Y είναι η μεταβλητή $ER\_{i,t}$ και Χ είναι η μεταβλητή $ER\_{M,t}$):
  
  $$ER\_{i,t} \= \\alpha \+ \\beta ER\_{M,t} \+ \\epsilon\_t$$
  
4. **Σχολιάστε τα μεγέθη και τα πρόσημα των εκτιμημένων συντελεστών $\\alpha$ και $\\beta$**. Είναι η μετοχή επιθετική ή αμυντική;
  
5. **Σχολιάστε το συντελεστή προσδιορισμού της παλινδρόμησης $R^2$** και σχολιάστε τον από κοινού έλεγχο στατιστικής σημαντικότητας (F-test).
  
6. **Σχολιάστε εάν οι εκτιμημένοι συντελεστές είναι στατιστικά σημαντικοί** σε επίπεδο σημαντικότητας 5% (t-statistic).
  
7. **Ελέγξτε την από κοινού υπόθεση ότι $\\alpha \= 0, \\beta \= 1$** σε 5% επίπεδο σημαντικότητας. Τι συμπέρασμα προκύπτει από το αποτέλεσμα του ελέγχου;
  
8. **Ελέγξτε τα κατάλοιπα της παλινδρόμησης για παραβίαση των παραδοχών της ομοσκεδαστικότητας και της μη-αυτοσυσχέτισης** και αναφέρετε τυχόν παραβιάσεις. Εκτιμήστε ξανά τη γραμμική παλινδρόμηση εκτιμώντας τυπικά σφάλματα επιλέγοντας τη κατάλληλη διόρθωση (White ή Newey-West) και σχολιάστε τις όποιες διαφορές.
  
9. **Δημιουργείστε μία ψευδομεταβλητή για θετικές και αρνητικές αποδόσεις της αγοράς**. Δηλαδή η ψευδομεταβλητή ($DUMMY\_M$) θα παίρνει την τιμή 1 όταν $R\_{M,t} \> 0$ και την τιμή 0 όταν $R\_{M,t} \\le 0$ (για ευκολία μπορείτε να χρησιμοποιήσετε το excel για τη δημιουργία της ψευδομεταβλητής κάνοντας χρήση της συνάρτησης IF). Στη συνέχεια εκτιμήστε την ακόλουθη παλινδρόμηση:
  
  $$ER\_{i,t} \= \\alpha \+ \\beta\_1 DUMMY\_M \+ \\beta\_2 DUMMY\_M \\cdot ER\_{M,t} \+ \\beta\_3 ER\_{M,t} \+ \\epsilon\_t$$

{{< /details >}}

{{< details summary="Εργασία σε κώδικα" >}}
```go 
	// Στα πλαίσια της μεθοδολογικής τεκμηρίωσης της εργασίας και
	// πέραν της χρήσης του στατιστικού πακέτου EViews 12, αναπτύχθηκε συμπληρωματικά αλγόριθμος γραμμικής παλινδρόμησης στη γλώσσα προγραμματισμού Go (Golang).
	// Ο κώδικας, ο οποίος παρατίθεται αναλυτικά στο παρόν Παράρτημα, δημιουργήθηκε για τους εξής σκοπούς:
	
	// 1. Επαλήθευση Αποτελεσμάτων: Ο κώδικας υπολογίζει εκ νέου τους συντελεστές α και β του υποδείγματος CAPM,
	// καθώς και τα στατιστικά μεγέθη $R^2$ και F-statistic, επιβεβαιώνοντας την ακρίβεια των αποτελεσμάτων που παρήγαγε το EViews.
	
	// 2. Αλγοριθμική Διαφάνεια: Μέσω της συνάρτησης calculateLinearRegression και calculateFTestForModelSignificance που περιλαμβάνονται στο αρχείο capm.go,
	// αποτυπώνεται η μαθηματική διαδικασία των Ελαχίστων Τετραγώνων (OLS) βήμα προς βήμα, χωρίς τη χρήση "black-box" συναρτήσεων,
	// αποδεικνύοντας την εις βάθος κατανόηση του υπολογιστικού υποβάθρου του μοντέλου.
	
	package main
	
	import (
		"encoding/csv"
		"fmt"
		"io"
		"log"
		"math"
		"os"
		"strconv"
		"strings"
	)
	
	// returns a single column of numbers from a csv file
	func floatReader(file string, recordColumn int, startRow int) []float64 {
	
		// use os.ReadFile to load the file into memory
		// Be careful with the os.ReadFile because it reads the whole file into memory.
		b, err := os.ReadFile(file)
		if err != nil {
			log.Fatal(err)
		}
	
		// `b` contains everything your file has.
		// This writes it to the Standard Out.
		// os.Stdout.Write(b)
	
		// read from csv - we convert the byte input from the file to string
		// added reader r configuration to use ; instead of , for comma
		r := csv.NewReader(strings.NewReader(string(b)))
		r.Comma = ';'
	
		var columnSlice []float64
	
		index := 0
	
		for {
			index += 1
			record, err := r.Read()
			if err == io.EOF {
				break
			}
			if err != nil {
				log.Fatal(err)
			}
			if index > startRow {
				x, err := strconv.ParseFloat(record[recordColumn], 64)
				if err != nil {
					log.Fatal(err)
				}
	
				columnSlice = append(columnSlice, x)
			}
			// fmt.Print(x)
			// fmt.Println(record)
	
		}
	
		return columnSlice
	}
	
	// calculate slope b and y-intercept a for simple linear regression (SLR)
	func calculateLinearRegression(y, x []float64) (a, b float64) {
		var sumX, sumY, meanX, meanY float64
	
		// y=a+bx: regression equation
		// assuming len(x) == len(y)
		for i, xValue := range x {
			sumX += xValue
			sumY += y[i]
		}
	
		meanX = sumX / float64(len(x))
		meanY = sumY / float64(len(y))
	
		var bNumerator, bDenominator float64
	
		for i, xValue := range x {
			bNumerator += (xValue - meanX) * (y[i] - meanY)
			bDenominator += math.Pow((xValue - meanX), 2)
		}
	
		// y=a+bx: regression equation
		b = bNumerator / bDenominator
		a = meanY - b*meanX
	
		return a, b
	}
	
	// HELPER - Calculate Sums of squares (total, regression, error): SST, SSR, SSE for simple linear regression
	// SST: Sum of squared differences between the observed dependent variables and the overall mean. SST measures the total variability of a dataset.
	// SSR: or explained SoS -Sum of squared differences between predicted value and mean of dependent variable. It describes how well our line fits the data.
	// SSE: or residual(unexplained) SoS, the difference between the observed and predicted values. Regres. Analys. aims to minimize SSE - 
	// smaller SSE, better prediction power.
	// SST = SSR + SSE
	func calculateSoS(LR_a, LR_b float64, y, x []float64) (sst, ssr, sse float64) {
		// SST = Sum[(y_i - meanY)^2]
		// SSR = Sum[(predicted_y_i - meanY)^2]
		// SSE = Sum[(ε_i)^2] = Sum[(y_i - predicted_y_i )^2]
		// predicted_yi = a + b*xi (y=a+bx: regression equation)
	
		var predicted_y_i, sum_y, mean_y float64
		var predicted_y []float64
	
		// sample = len(x)
		for i, x_i := range x {
			// calculate y_i
			predicted_y_i = LR_a + LR_b*x_i
			predicted_y = append(predicted_y, predicted_y_i)
	
			// calculate sum
			sum_y += y[i]
		}
	
		// calculate sample mean y
		mean_y = sum_y / float64(len(y))
	
		// calculate SSR and SST
		for i := range predicted_y {
			ssr += math.Pow((predicted_y[i] - mean_y), 2)
			sst += math.Pow((y[i] - mean_y), 2)
	
		}
	
		sse = sst - ssr
	
		return sst, ssr, sse
	}
	
	func calculateRSquared(sst, ssr float64) (rSquared float64) {
		// R^2 = SSR/SST
	
		// calculate R squared
		rSquared = ssr / sst
	
		return rSquared
	}
	
	// Calculate F-statistic for SLR. This tests the joint null hypothesis - all slope coefficients (=0)
	//
	// F-statistic measures overall model significance - do the independent variables
	// explain a significant portion of the variation in the dependent variable?
	//
	// J = no of restrictions, N = no of observations(sample), K = no of coefficients(b)
	//
	// The larger the F-statistic, the stronger the predicitive power of the explanatory variables jointly.
	//
	// The Prob(F-statistic) is the p-value associated with the F-test. Returns the probability that a larger F-stat. is returned (of H0 == true).
	// If Prob(F-statistic) < 0.05, the model is statistically significant at the 5% level.
	func calculateFTestGeneral(sse_r, sse_u float64, j, n, k int) (f_value float64) {
		// SSE = SST-SSR
		// General: F = [(SSE_R - SSE_U) / J] / [SSE_U / (N-K)]
		// Simplified: F = [(SST - SSE) / (K-1)] / [SSE / (N-K)]
		// J = no of restrictions, N = no of observations, K = no of coefficients
	
		// calculate
		f_value = ((sse_r - sse_u) / float64(j)) / (sse_u / float64(n-k))
	
		return f_value
	}
	
	// Simplified: F = [(SST - SSE) / (K-1)] / [SSE / (N-K)]
	// J = no of restrictions, N = no of observations, K = no of coefficients
	func calculateFTestForModelSignificance(sst, sse float64, n, k int) (f_value float64) {
		// SSE = SST-SSR
		// General: F = [(SSE_R - SSE_U) / J] / [SSE_U / (N-K)]
		// Simplified: F = [(SST - SSE) / (K-1)] / [SSE / (N-K)]
		// J = no of restrictions, N = no of observations, K = no of coefficients
	
		// calculate
		f_value = ((sst - sse) / float64(k-1)) / (sse / float64(n-k))
	
		return f_value
	}
	
	func main() {
	
		excessMSFT := floatReader("project_data/excess-473.csv", 0, 1)
		excessMrkt := floatReader("project_data/excess-473.csv", 1, 1)
	
		a, b := calculateLinearRegression(excessMSFT, excessMrkt)
	
		sst, ssr, sse := calculateSoS(a, b, excessMSFT, excessMrkt)
	
		R2 := calculateRSquared(sst, ssr)
	
		fstat := calculateFTestForModelSignificance(sst, sse, 473, 2)
		fmt.Print(len(excessMSFT), a, b, R2, fstat)
	
	}
```
{{< /details >}}
