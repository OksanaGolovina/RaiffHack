Решение основано на алгоритме LightAutoML с дополнительным обогащением данных из открытых источников (Росстат).  


- Проведен EDA инструментами pandas_profile и сравнениями корреляции метрик разными методами в зависимости от фичей  - 
Pandas profiling - https://drive.google.com/file/d/1xQl3LvpX9J0G6gJoaBjzRcBFKZi6QZXz/view?usp=sharing
- Введены дополнительные метрики: премиальность этажей и типирование города  
- Использованы дополнительные стат данные (среднемесячная заработная плата и численность населения по регионам, Источник: Росстат);
- Учтен дисконт, закладываемый при ручном расчете (использовали вариант из публичного решения, ссылка на github: https://github.com/BatyaZhizni/Raifhack-DS)


Для обогащения данных использованы дополнительные датасеты:


1. zarplaty.xlsx - Среднемесячная номинальная начисленная заработная плата работников в целом по экономике по субъектам Российской Федерации за 2000-2020 гг. Источник: Росстат, https://rosstat.gov.ru/labor_market_employment_salaries Ссылка - https://docs.google.com/spreadsheets/d/1S1ORmz2W4QTG-d8odUOqT6Czu21NF2Vw/edit?usp=sharing&ouid=108685579276627434305&rtpof=true&sd=true
2. zarplaty.xlsx - Численность населения по населенным пунктам России. Источник: Росстат, https://rosstat.gov.ru/folder/12781.  Ссылка: https://drive.google.com/file/d/19hJI_zlTZboxSh_JwPrWt8vYx9lkNlM0/view?usp=sharing


Для обучения использовали модель LightAutoML*


1. LightAutoML project from Sberbank AI Lab AutoML group is the framework for automatic classification and regression model creation.


Authors: Alexander Ryzhkov, Anton Vakhrushev, Dmitry Simakov, Vasilii Bunakov, Rinchin Damdinov, Pavel Shvets, Alexander Kirilin


2. Библиотеки
!pip install https://github.com/pandas-profiling/pandas-profiling/archive/master.zip
import pandas as pd
import numpy as np
import typing
import torch
import matplotlib.pyplot as plt


!pip install -U lightautoml
from sklearn.model_selection import train_test_split
from lightautoml.automl.presets.tabular_presets import TabularUtilizedAutoML
from lightautoml.tasks import Task
© 2021 GitHub, Inc.
Terms
Privacy
Security
Status
Docs
Contact GitHub
Pricing
API
Training
Blog
About
