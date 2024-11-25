1. Постановка задачи
Разработать решение, которое позволит персонализировать предложения постоянным клиентам компании «В один клик» (продажа товаров для детей, для дома, мелкой бытовой техники, косметики и продуктов), чтобы увеличить их покупательскую активность.
1.1. Нужно промаркировать уровень финансовой активности постоянных покупателей:
- «снизилась», если клиент стал покупать меньше товаров;
- «прежний уровень».
1.2. Собрать данные по клиентам по следующим группам:
- Признаки, которые описывают коммуникацию сотрудников компании с клиентом.
- Признаки, которые описывают продуктовое поведение покупателя.
- Признаки, которые описывают покупательское поведение клиента.
- Признаки, которые описывают поведение покупателя на сайте.
1.3.1 Нужно построить модель, которая предскажет вероятность снижения покупательской активности клиента в следующие три месяца.
1.3.2 В исследование нужно включить дополнительные данные финансового департамента о прибыльности клиента: какой доход каждый покупатель приносил компании за последние три месяца.
1.3.3 Используя данные модели и данные о прибыльности клиентов, нужно выделить сегменты покупателей и разработать для них персонализированные предложения.

2. Используемые модели
Были обучены четыре модели с различным набором гиперпараметров:
DecisionTreeClassifier
KNeighborsClassifier
LogisticRegression
SVC

3. Результат применения моделей.
Для оценки качества модели была выбрана метрика ROC-AUC, т.к. она оценивает качество решений модели в наиболее общем виде, учитывая все возможные пороговые значения. Это самая общая оценка итогов работы модели.
!!! Для выбора лучшей модели использовался общий пайплайн для всех моделей и инструмент подбора гиперпараметров, который вернул лучшую модель: SVC(C=1, kernel='poly', probability=True)

commit#2
!!! Модель LogisticRegression решено исключить т.к. возможно данные содержат множество взаимодействий между признаками, и логистическую регрессию будет сложно настроить для учета всех этих взаимодействий без значительного увеличения сложности
модели.
!!! Для выбора лучшей модели использовался общий пайплайн для всех моделей и инструмент подбора гиперпараметров, который вернул лучшую модель: SVC(C=1, kernel='poly', probability=True)

commit#3
!!! Модель LogisticRegression решено вернуть, т.к. понизилась метрика ROC-AUC.
Решено исключить модель SVC из-за
- высокая вычислительная сложности: SVC может быть медленным при работе с большими наборами данных.
- чувствительности к выбору параметров: модель SVC чувствительна к параметрам, таким как параметр регуляризации C и параметры ядра. Неправильный выбор этих параметров может привести к переобучению или недоучиванию модели.
- проблемой с интерпретируемостью: в отличие от линейной регрессии или деревьев решений, SVC сложнее интерпретировать. Это делает его менее подходящим для задач, где важна прозрачность модели.
