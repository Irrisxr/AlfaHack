# AlfaHack

#### Команда:
**TeamLead:** Александр Олейников
- Максим Труфанов
- Матвей Савченков
- Екатерина Мустаева
- Амаль Хатуев

#### Вычислительные ресурсы
Работа выполнялась с использованием бесплатного сервиса Kaggle с конфигурациями:
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
### Предобработка данных и отбор признаков
  ... 
### Построение модели
![image](https://github.com/user-attachments/assets/1f004f57-3a5f-4905-82d1-6c950e729e17)

<img width="16384" alt="ALFA HACK" src="https://github.com/user-attachments/assets/ab2a651f-5215-4305-9e73-58cdd9d6d3b6">

