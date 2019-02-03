# Monte-Carlo-method using python3
**Task**
The company makes some articles. The article production cost is 10 Euro. The article price (i.e. the company income) is 15 Euro.
The article can have defects of two types, denoted as defects A and B. The defects are not related between each other; so, they are possible in any combina-tions. The defect A exists in 6% of articles; the defect B, in 8%. If an article has only one defect, the attempt is made to repair it; the cost of repair is 3 Euro. The repair is successful in 70% of cases; in other cases, the defect cannot be eliminat-ed. If an article has two defects, it is rejected (i.e. it is not repaired and not sold). In case of an unsuccessful repair, an article is also rejected (i.e. it is not sold).
You must find: 
a) average profit resulting from making one article; 
b) the probability of making a good article.

```
import random


n = 1000
cost = 10 #Euro
price = 15 #Euro
defect_A = 0.06 #The defect A exists in 6% of articles
defect_B = 0.08 #The defect B exists in 8% of articles
repair_success = 0.7 #The repair is successful in 70% of cases
repair_cost = 3 #Euro

profit = 1
good = 1
for x in range(1000):
    profit = profit - cost
    rnd1 = random.uniform(0, 1) # 1st random number
    rnd2 = random.uniform(0, 1) # 2nd random number

    if rnd1 < defect_A and rnd2 < defect_B:
        continue 

    if (rnd1 < defect_A and rnd2 > defect_B) or (rnd1 > defect_A and rnd2 < defect_B):
            profit -= repair_cost

            rnd3  = random.uniform(0, 1) # 3d random number
            if rnd3 < repair_success:
                profit += price
                good += 1 # counting goood articles
    if rnd1 > defect_A and rnd2 > defect_B:
        profit += price
        good += 1
    
aver_good = (good / n) * 100
aver_profit = (profit / n)
print('The probability of making a good article:',int(aver_good),'%')                
print('Average profit:',int(aver_profit),'Euro')        

```
