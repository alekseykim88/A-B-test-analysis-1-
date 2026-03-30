# A-B-test-analysis-1-
New Onboarding

| user_id | group | converted |
| ------- | ----- | --------- |
| 1       | A     | 0         |
| 2       | A     | 1         |
| 3       | B     | 0         |

p-value = 0.08
Задача -  Можно ли внедрять новый onboarding?

#считаю общее количество конверсий, конверсию и группирую по группам

Select group, count(distinct user_id) as users,
sum(converted) as converstions,
sum(converted)*1.0/count(distinct user_id) as conversion
FROM AB_test
GROUP BY group;

полученные данные:
GROUP A
- users 1000
- conversions 100
- conversion 10%
GROUP B
- users 1000
- conversions 120
- conversion 12%
размер эффекта 2%

  На данный момент недостаточно доказательств для внедрения. 
  P-value>0.05 - эффект не является значимым. 
  Также рандомизация некорректна - группы отличаются по размеру.
  Возможны ошибки 2 типа - ложноотрицательные.
