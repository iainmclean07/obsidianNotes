
		




|              | Intimate   | Personal | Social | Public | Total |
| ------------ | ---------- | -------- | ------ | ------ | ----- |
| Face-to-Face | 70 E= 0.51 | 850      | 50     | 30     | 1000  |
| Hybrid       | 65         | 875      | 30     | 30     | 1000  |
| Total        | 135        | 1725     | 80     | 60     | 2000  |
|              |            |          |        |        |       |



|          | Face-to-Face | Hybrid    | Total      |
| -------- | ------------ | --------- | ---------- |
| Intimate | 70 E=60      | 65 E=60   | 135 (6%)   |
| Personal | 850 E=860    | 875 E=860 | 1725 (86%) |
| Social   | 50 E=40      | 30 E=40   | 80 (4%)    |
| Public   | 30 E=30      | 30 E=30   | 60 (3%)    |
| Total    | 1000         | 1000      | 2000       |


H0: Proxemics are the same
H1:  Proxemics are different

significance level = 1%


Find the distance between the expected value and the actual value 

X^2 = (Actual Value - Expected Value)^2 / Expected Value + (Actual Value - Expected Value)^2 / Expected Value ... For each of the rows and columns

X^2 = (70 - 60)^2 / 60 + (65 - 60)^2 / 60 + (850 - 860)^2 / 860 .... = 7.46124031008

bins = [0, .46, .76, 1.2, 2.1, 3.6, 7.6]

DoF = (rows - 1)(cols - 1) = (4 - 1)(2 - 1) = 3

critical value = 11.34

Cannot reject the null hypothesis 

Effect size in this case is Cramer's V which = 

V = sqrt(Chi Square Value / sample size * min (rows - 1, cols - 1))

V = sqrt (7.46124031008 / 2000 * 1) = 0.00373