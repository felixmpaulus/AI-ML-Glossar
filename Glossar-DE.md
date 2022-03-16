# AI-ML-Glossar

**AdaBoost**
- erstellt einen Forest.
- i.d.R. haben alle Knoten nur 2 Kanten (Stump).
- die Trees werden nicht unabhängig voneinander gebaut. Ein Tree (bzw. dessen Fehler) hat Einfluss auf die Berechnung des nächsten Trees.
- im Gegensatz zum Random Tree haben die Trees gewichteten Einfluss auf die Berechnung des Labels.
- Durchführung:
    1. jeder Zeile wird ein Gewicht zugeteilt (zu Beginn sind alle Gewichte gleich, also 1/N).
    2. für jede Spalte wird die Gini-Impurity berechnet, die Spalte mit geringster Gini-Impurity wird als erster fertiger Tree gespeichert.
    3. der Error eines Trees berechnet sich aus der Summe aller Zeilengewichte der Zeilen, die der Tree falsch zuordnet (0 <= Error <= 1).
    4. der 'amount of say' dieses Trees wird jetzt durch eine Log_e-Funktion des Errors berechnet (Error gegen 0 -> großer 'amount of say').
    5. nun werden die Gewichte aller Zeilen angepasst:
        1. die Zeilen, die falsch zugeordnet wurden, werden mit e^(amount of say) skaliert.
        2. die Zeilen, die korrekt zugeordnet wurden, werden mit e^-(amount of say) skaliert.
        3. abschließend müssen alle Gewichte normalisiert werden.
    6. jetzt wird ein neuer Datensatz gebildet.
        1. eine zufällige Zahl sei wiederholt gegeben bis der neue Datensatz so groß wie der alte Datensatz ist.
        2. es wird die Zeile in den neuen Datensatz übertragen, deren Gewicht (aufsummiert mit allen vorherigen Gewichten) >= der zufälligen Zahl ist (hohes Gewicht -> hohe Wahrscheinlichkeit (ggfs. mehrfach) übertragen zu werden).
    7. ab Schritt 2 wird wieder ein neuer Tree erstellt (die Spalte des ersten Trees bleibt erhalten) und anschließend werden erneut die Gewichte angepasst (im originalen Datensatz).
    8. Wenn jetzt ein Datensatz von allen Trees zugeordnet wird, dann wird die Summe der 'amount of says' aller Trees mit derselben Zuordnung aufsummiert. Die Zuordnung mit der höchsten Summe gewinnt.
- https://www.youtube.com/watch?v=LsK-xG1cLYA&ab_channel=StatQuestwithJoshStarmer


**Bagging (Randm Forest Tree)**
- wenn k Trees erstellt wurden um Overfitting zu vermeiden (Random Forest), erhält man für jeden neuen Datensatz auch k Antworten/Labels.
- **B**ootstrapping **AGG**regate beschreibt die Annahme, das das Label mit der höchsten Häufigkeit das finale\korrekte Label ist.


x **Bedingte Wahrscheinlichkeit**


x **BIAS** (vs. Varianz)


x **CART (Classification and Regression Trees)**


x **Censoring**
    -> Left censoring – a data point is below a certain value but it is unknown by how much.
    -> Interval censoring – a data point is somewhere on an interval between two values.
    -> Right censoring – a data point is above a certain value but it is unknown by how much.


**Classification Tree**
- innerhalb des Baumes kann auf verschiedene Datentypen geprüft werden (logicals, numerical).
- dieselbe Spalte kann an mehreren Knoten abgefragt werden.
- dieselbe Klasse kann an mehreren Knoten klassifiziert werden.
- Durchführung:
    1. für jede Predictor-Klasse jeder Spalte der Daten, wird via dem Gini-Koeffizient berechnet, wie gut diese Predictor-Klasse jede Outcome-Klasse predictet.
    2. die Gini-Impurity wird dann über alle Predictor-Klassen gewichtet (Anzahl Zeilen jeder Predictor-Klasse / Anzahl aller Zeilen) und aufsummiert (Totale Gini).
    3. die Spalte mit der geringsten Gini-Impurity wird als Root gewählt und die Daten entsprechend aufgeteilt.
    4. dieser Prozess (Aufteilung nach Spalte mit geringster Gini-Impurity) wird so lange wiederholt, bis ein festgelegter minimaler Treshold an vom Knoten beschriebenen Daten erreicht ist. Anschließend wird nicht weiter unterteilt, selbst wenn die Gini-Impurity > 0 ist.
    5. ist der Treshold erreicht und die Gini-Impurity > 0, wird die mit der Klasse klassifiziert, welche am häufigsten vorkommt.
- https://www.youtube.com/watch?v=_L39rN6gz7Y
- Der C4.5 Algorithmus kann genutzt werden. Dieser ermöglicht zusätzliches Pruning.


**Corrective maintenance**
- Wartung, nachdem ein Versagen oder eine Fehlfunktion eingetreten ist.


x **Cox Regression**


x **Cross-Validation**


x **Datenstrukturen (ordinal, continuous, ...)**


**Decision Trees**
- classification tree -> unterteilt Daten in Klassen.
- regression tree -> unterteilt Daten in numerische Bereiche.
- Teil des Supervised Machine Learning, wobei ein Bezug zwischen Input Variable und Target Varibale erlernt wird, welcher durch einen Entscheidungsbaum repräsentiert werden kann. Klassifizierung eines Inputs erfolgt dann über eine Abfolge von Tests (logical or numerical).


x **Effect-Size (und Beziehung zur HR)**


x **Ereigniszeitanalyse**


**Gini-Koeffizient / Gini-Impurity**
- gegeben ein klassifizierter Predictor (eine Spalte) und ein vielzahl von klassifizierten Outcomes J.
- für jede Klasse des Predictors berechnet sich die Gini-Impurity aus 1 minus der Summe aller Wahrscheinlichkeiten (Anteile) zum Quadrat.
- für die gesamte Predictor-Spalte berechnet sich die totale Gini-Impurity aus der gewichteten Summe der Gini-Impurities aller Predictor-Klassen.
- gewichtet wird dabei mit dem prozentualen Anteil der Predictor-Klasse an der Predictor-Spalte.
- für einen numerischen Predictor siehe Video:
- https://www.youtube.com/watch?v=_L39rN6gz7Y
- https://en.wikipedia.org/wiki/Decision_tree_learning#Gini_impurity


**Gradient Boost for Classification**
- ähnlich zu AdaBoost, ein Forest wird gebaut.
- die Trees werden nicht unabhängig voneinander gebaut. Ein Tree (bzw. dessen Fehler) hat Einfluss auf die Berechnung des nächsten Trees.
- die einzelnen Trees wachsen nur bis zu einer festgelegten Größe (8 bis 32 Blattknoten üblich).
- 'Gradient' weil das Residuum auf der Ableitung der Loss-Funktion nach dem Predictor basiert ((0.5*(outcome-predicted))^2)' = -(outcome-predicted) = Error)
- Durchführung:
    1. das durchschnittliche Outcome wird berechnet (erster Tree, nur ein Knoten).
    2. der Fehler (Residual) des ersten Trees (einfache Differenz zw. Durchschnitt und Outcome) wird an jede Zeile angehängt.
    3. jetzt wird klassisch ein Tree berechnet, welcher das Residuum predictet, nicht das Outcome.
    4. durch die festgelegte Tiefe können mehrere Zeilen in Blattknoten gruppiert werden. Hier wird der Durchschnitt gebildet.
    5. Um einen Datensatz zuzuordnen, wird dieser durch den ersten Tree berechnet (nur ein Knoten, immer der Durchschnitt des Outcomes), dann wird jeder weitere Tree (skaliert mit einer learningrate 0 <= l <= 1>) dazu addiert.
    6. mit der neu berechneten Zuordnung wird nun erneut der Fehler (Residual) gebildet und jeder Zeile angehängt.
    7. wieder bei Schritt 3 beginnen, so oft durchführen bis keine Verbesserung mehr oder eine festgelegte Zahl an Durchführungen (z.B. 100 Trees) erreicht ist.
    8. 
- viele Durchführungen mit geringer learningrate führen zu besseren Ergebnissen.
- https://www.youtube.com/watch?v=jxuNLH5dXCs


**Gradient Boost for Regression**
- ähnlich zu AdaBoost, ein Forest wird gebaut.
- die Trees werden nicht unabhängig voneinander gebaut. Ein Tree (bzw. dessen Fehler) hat Einfluss auf die Berechnung des nächsten Trees.
- die einzelnen Trees wachsen nur bis zu einer festgelegten Größe (8 bis 32 Blattknoten üblich).
- 'Gradient' weil das Residuum auf der Ableitung der Loss-Funktion nach dem Predictor basiert ((0.5*(outcome-predicted))^2)' = -(outcome-predicted) = Error)
- Durchführung:
    1. das durchschnittliche Outcome wird berechnet (erster Tree, nur ein Knoten).
    2. der Fehler (Residual) des ersten Trees (einfache Differenz zw. Durchschnitt und Outcome) wird an jede Zeile angehängt.
    3. jetzt wird klassisch ein Tree berechnet, welcher das Residuum predictet, nicht das Outcome.
    4. durch die festgelegte Tiefe können mehrere Zeilen in Blattknoten gruppiert werden. Hier wird der Durchschnitt gebildet.
    5. Um einen Datensatz zuzuordnen, wird dieser durch den ersten Tree berechnet (nur ein Knoten, immer der Durchschnitt des Outcomes), dann wird jeder weitere Tree (skaliert mit einer learningrate 0 <= l <= 1>) dazu addiert.
    6. mit der neu berechneten Zuordnung wird nun erneut der Fehler (Residual) gebildet und jeder Zeile angehängt.
    7. wieder bei Schritt 3 beginnen, so oft durchführen bis keine Verbesserung mehr oder eine festgelegte Zahl an Durchführungen (z.B. 100 Trees) erreicht ist.
    8. 
- viele Durchführungen mit geringer learningrate führen zu besseren Ergebnissen.
- https://www.youtube.com/watch?v=2xudPOBz-vs


x **Hazard-function**


x **Hazard-ratio**


x **Kaplan-Meier plot**


x **Konfidenzintervall**
    -> https://studyflix.de/statistik/konfidenzintervall-1580


x **Kumulative Inzidenz**


x **Kurtosis**


x **Logistical Regression**


x **Logrank test**
    ->https://www.ncbi.nlm.nih.gov/pmc/articles/PMC403858/#ref3
    -> https://www.ncbi.nlm.nih.gov/pmc/articles/PMC1065034/


x **Multivariate Statistical Modelling**


x **Nullhypothese**


x **p-wert**


x **Parametric Test/ Non-Parametric Test**


**Preventive Maintenance**
- Wartung, bevor ein Versagen oder eine Fehlfunktion eingetreten ist. Ziel ist die Reduzierung der Wahrscheinlichkeit eines Versagens oder einer Fehlfunktion.


x **Proportionalität (Statistik)**


**Random Forests**
- basiert auf Decision Trees
- Durchführung:
    1. wir erstellen ein bootstrapped Dataset indem zufällig ausgewählte Zeilen aus dem originalem Dataset ausgewählt werden (mehrfache Auswählung ist möglich, i.d.R. fehlen 1/3 der Daten im Bootstrapped Dataset)
    2. anschließend wird ein Decision Tree erstellt, allerdings mit Einschränkungen:
    3. jede Einteilung erfolgt auch hier nach der Predictor-Spalte mit der geringsten Gini-Impurity, allerdings nicht unter allen, sondern unter n zufällig ausgewählten Spalten des Bootstrapped Datasets (n i.d.R. Wurzel der Spaltenmenge).
    4. dieser Prozess wird k mal wiederholt, jedes Mal entsteht ein neuer Decision Tree.
    5. um Data zu lablen, wird diese mit allen k Trees untersucht und die häufigste Antwort als korrekt angenommen (s. Bagging), jeder Tree hat dabei denselben Einfluss auf das Label
    6. mit den originalen Datensätzen können die Trees jetzt getestet werden
- durch Anpassen von n (Anzahl zufällig gewählter Spalten) kann der Random Forest jetzt optimiert werden


x **Linear Regression**


**Regression Tree**
- binärer Entscheidungsbaum, welcher die Datenmenge durch Regression 'klassifiziert'.
- binär heißt, jeder Knoten hat genau 2 Kanten.
- Durchführung:
    1. für jede Spalte der Daten, welche das Outcome predictet, wird via linearer Regression berechnet, was der minimal mögliche Fehler bei Aufteilung in 2 Datenmengen bzgl. dieses Predictors wäre.
    2. die Spalte mit dem minimalen möglichen Fehler wird als Root gewählt und aufgeteilt (deswegen binär).
    3. für die dabei entstandenen 2 Teilmengen wird erneut die lineare Regression angewandt um diese weiter zu unterteilen.
    4. unterschreitet die Größe einer Teilmenge einen Treshold (z.B. 20 Datenpunkte), wird diese nicht erneut aufgeteilt, und ihr durchschnittlicher Outcome als Blattknoten hinzugefügt.
- https://www.youtube.com/watch?v=g9c66TUylZ4&


x **Rule Learning**
- Teil des Supervised Machine Learning, wobei ein Bezug zwischen Input Variable und Target Varibale erlernt wird, welcher durch einen Satz von Regeln repräsentiert werden kann. Die Klassifizierung erfolgt hier über ein Abgleichen des Inputs mit den erlernten Regeln (logical/numerical).
The RIPPER (Repeated Incremental Pruning to Produce Error Reduction) algorithm can be used.


x **T-Verteilung vs. Normalverteilung**


x **Überlebensfuntion**


x **Varianz** (vs. Bias)


x **Weibull-Modell**











