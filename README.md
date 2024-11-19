# AlfaHack

### Результат:

![image](https://github.com/user-attachments/assets/f516f513-e7af-4c62-a1b5-03ab278f3534)

#### Команда DRUJBA:
**TeamLead:** Александр Олейников
- Максим Труфанов
- Матвей Савченков
- Екатерина Мустаева
- Амаль Хатуев

#### Вычислительные ресурсы
Работа выполнялась с использованием бесплатного сервиса Kaggle с конфигурацией:
 - СPU 4 core
 - GPU P100 16GB / GPU T4 15GB x2
 - RAM 29 GB
 - DISK 57.6 GB 

## Задача:
**Кейс:** Склонность физического лица к инвестициям.

Определите склонность и заинтересованность физических лиц в инвестициях, основываясь на данных о клиенте и их оценке банком, представленных в числовом формате. Для этого обработайте данные с результатами оценки, обучите модель и оцените качество вашей модели и ее предсказаний по метрике roc-auc.

#### Данные

- 10 тренировочных датасетов, пронумерованных в формате train_номер.csv.
- 10 тестовых датасетов, пронумерованных в формате test_номер.csv.

Каждый из файлов датасетов содержит следующие признаки:
- ID — уникальный анонимный идентификатор клиента;
- smpl — признак, указывающий на то, к какой выборке относятся данные (train либо test);
- target — целевое значение, которое вы должны спрогнозировать;
- 500 признаков для обучения модели в формате feature_i, где i — номер конкретного признака по порядку.

## Решение
- Rawdata.parquet - файл с объеденёнными train файлами.
- features_with_logit/features.json из файла - берутся категориальные признаки.
- ultra_mega_last_features.json - итоговый набор признаков.
- Feature_Selection.ipynb - отбор признаков.
- Building_models.ipynb - построение моделей.

### Предобработка данных и отбор признаков.
1. Обор признаков через feature_selection из Библиотеки CatBoost. Взяли топ 200.
2. С помощью тернарного поиска определили оптимальное кол-во признаков 172.

Пробовали:
1. Удаление сильно коррелирующих признакоов.
2. Отбор признаков на основе feature_importance.
3. Отбор признаков на основе Logit модели.
4. Генерацию признаков ^2 и exp.
   
### Построение модели
Модель состоит из двух усреднённых ансамблей для повышения вариативности модели и улучшения стабильности предсказания:
1. 10 моделей CatBoost с разным random_state(другие параметры идентичны).
2. 3 модели XGBoost с разными параметрами.

Итоговое предсказание формировалось на основе предсказаний двух этих ансамблей с весами 0.5.

Пробовали:
1. Обучать модели CatBoost через Spark и XGBoost с помощью dask на всех данных и признаках.
2. Полносвязную нейронную сеть.
3. Обучать модели, которые хорошо работают с дисбалансом классов из библиотеки imblearn и модели AdaBoost, NaiveBayes, LightGBM и RandomForest.
4. Также пробовали метод ансамблирования - bagging.
 
![image](https://github.com/user-attachments/assets/1f004f57-3a5f-4905-82d1-6c950e729e17)
