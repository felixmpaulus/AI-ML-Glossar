# AI-ML-Glossar

**AdaBoost**


x **CART (Classification and Regression Trees)**


**Regression Tree**
- binärer Entscheidungsbaum, welcher die Datenmenge durch Regression 'klassifiziert'.
- binär heißt, jeder Knoten hat genau 2 Kanten.
- für jede Spalte der Daten, welche das Outcome predictet, wird via linearer Regression berechnet, was der minimal mögliche Fehler bei Aufteilung in 2 Datenmengen bzgl. dieses Predictors wäre.
- die Spalte mit dem minimalen möglichen Fehler wird als Root gewählt und aufgeteilt (deswegen binär).
- für die dabei entstandenen 2 Teilmengen wird erneut die lineare Regression angewandt um diese weiter zu unterteilen.
- unterschreitet die Größe einer Teilmenge einen Treshold (z.B. 20 Datenpunkte), wird diese nicht erneut aufgeteilt, und ihr durchschnittlicher Outcome als Blattknoten hinzugefügt.
- https://www.youtube.com/watch?v=g9c66TUylZ4&

**Classification Tree**
- innerhalb des Baumes kann auf verschiedene Datentypen geprüft werden (logicals, numerical).
- dieselbe Spalte kann an mehreren Knoten abgefragt werden.
- dieselbe Klasse kann an mehreren Knoten klassifiziert werden.
- für jede Predictor-Klasse jeder Spalte der Daten, wird via dem Gini-Koeffizient berechnet, wie gut diese Predictor-Klasse jede Outcome-Klasse predictet.
- die Gini-Impurity wird dann über alle Predictor-Klassen gewichtet (Anzahl Zeilen jeder Predictor-Klasse / Anzahl aller Zeilen) und aufsummiert (Totale Gini).
- die Spalte mit der geringsten Gini-Impurity wird als Root gewählt und die Daten entsprechend aufgeteilt.
- dieser Prozess (Aufteilung nach Spalte mit geringster Gini-Impurity) wird so lange wiederholt, bis ein festgelegter minimaler Treshold an vom Knoten beschriebenen Daten erreicht ist. Anschließend wird nicht weiter unterteilt, selbst wenn die Gini-Impurity > 0 ist.
- ist der Treshold erreicht und die Gini-Impurity > 0, wird die mit der Klasse klassifiziert, welche am häufigsten vorkommt.
- https://www.youtube.com/watch?v=_L39rN6gz7Y
- Der C4.5 Algorithmus kann genutzt werden. Dieser ermöglicht zusätzliches Pruning.

**Corrective maintenance**
- Wartung, nachdem ein Versagen oder eine Fehlfunktion eingetreten ist.

x **Cross-Validation**

**Decision Trees**
- classification tree -> unterteilt Daten in Klassen.
- regression tree -> unterteilt Daten in numerische Bereiche.
- Teil des Supervised Machine Learning, wobei ein Bezug zwischen Input Variable und Target Varibale erlernt wird, welcher durch einen Entscheidungsbaum repräsentiert werden kann. Klassifizierung eines Inputs erfolgt dann über eine Abfolge von Tests (logical or numerical).

**Gini-Koeffizient / Gini-Impurity**
- gegeben ein klassifizierter Predictor (eine Spalte) und ein vielzahl von klassifizierten Outcomes J.
- für jede Klasse des Predictors berechnet sich die Gini-Impurity aus 1 minus der Summe aller Wahrscheinlichkeiten (Anteile) zum Quadrat.
- für die gesamte Predictor-Spalte berechnet sich die totale Gini-Impurity aus der gewichteten Summe der Gini-Impurities aller Predictor-Klassen.
- gewichtet wird dabei mit dem prozentualen Anteil der Predictor-Klasse an der Predictor-Spalte.
- für einen numerischen Predictor siehe Video:
- https://www.youtube.com/watch?v=_L39rN6gz7Y
- https://en.wikipedia.org/wiki/Decision_tree_learning#Gini_impurity

**Preventive Maintenance**
- Wartung, bevor ein Versagen oder eine Fehlfunktion eingetreten ist. Ziel ist die Reduzierung der Wahrscheinlichkeit eines Versagens oder einer Fehlfunktion.

**Random Forests**
- build on decision trees

x **Rule Learning**
- Teil des Supervised Machine Learning, wobei ein Bezug zwischen Input Variable und Target Varibale erlernt wird, welcher durch einen Satz von Regeln repräsentiert werden kann. Die Klassifizierung erfolgt hier über ein Abgleichen des Inputs mit den erlernten Regeln (logical/numerical).
The RIPPER (Repeated Incremental Pruning to Produce Error Reduction) algorithm can be used.






**BIAS** (vs. Varianz)
**Bedingte Wahrscheinlichkeit**
**Cox Regression**
**Censoring**
    -> Left censoring – a data point is below a certain value but it is unknown by how much.
    -> Interval censoring – a data point is somewhere on an interval between two values.
    -> Right censoring – a data point is above a certain value but it is unknown by how much.
**Datenstrukturen (ordinal, continuous, ...)**
**Effect-Size (und Beziehung zur HR)**
**Ereigniszeitanalyse**
**Hazard-function**
**Hazard-ratio**
**Kaplan-Meier plot**
**Konfidenzintervall**
    -> https://studyflix.de/statistik/konfidenzintervall-1580
**Kumulative Inzidenz**
**Kurtosis**
**logrank test**
    ->https://www.ncbi.nlm.nih.gov/pmc/articles/PMC403858/#ref3
    -> https://www.ncbi.nlm.nih.gov/pmc/articles/PMC1065034/
**Multivariate Statistical Modelling**
**Nullhypothese**
**p-wert**
**Parametric Test/ Non-Parametric Test**
**Regression**
**Proportionalität (Statistik)**
**T-Verteilung vs. Normalverteilung**
**Überlebensfuntion**
**Varianz** (vs. Bias)
**Weibull-Modell**




