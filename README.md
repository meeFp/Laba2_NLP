# **Использование глубоких нейронных сетей для синтеза текста: анализ эффективности в создании естественно звучащих текстов.**
## Описание
### Цель:
Использовать глубокие нейросети модель для синтеза текста: анализ эффективности в создании естественно звучащих текстов.
### О проекте:
Этот проект демонстрирует использование библиотеки Tortoise TTS([Tortoise TTS](https://github.com/jnordberg/tortoise-tts)) для синтеза речи на основе глубоких нейронных сетей. В проекте используется модель Tortoise([Tortoise](https://huggingface.co/ken2ki/tortoise)) и предоставляется пример работы с пользовательским голосом. В данной работе использовался мой собственный голос, как датасэт(Голос.zip([Госол.zip](https://github.com/meeFp/Laba2_NLP/blob/main/Голоса.zip)))


## Используемые библиотеки

- tensorflow
- tensorflow_hub
- tensorflow_io

## Инструкции по установке:
1. Скачайте датасет ESC-50([ESC-50](https://github.com/karolpiczak/ESC-50))
2. Разархивируйте скачанный архив и поместите в гугл диск
3. Установите необходимые библиотеки, выполнив следующие команды:
   ```python
    %pip install tensorflow_io==0.31.0
    %pip install tensorflow==2.11.0
    %pip install tensorflow_hub
    ```

    ```python
    import os

    from IPython import display
    import matplotlib.pyplot as plt
    import numpy as np
    import pandas as pd

    import tensorflow as tf
    import tensorflow_hub as hub
    import tensorflow_io as tfio
    ```
4. Загрузить модель YAMNet:

   ```python
    yamnet_model_handle = 'https://tfhub.dev/google/yamnet/1'
    yamnet_model = hub.load(yamnet_model_handle)
   ```
## Примечательные особенности:
- Используется модель YAMNet для извлечения вложений из аудиофайлов
- Проект предоставляет инструкции по обучению собственной нейронной сети и тестированию собственных аудиофайлов
- Реализована предобработка данных, обучение модели и оценка результатов
- laba1_NN представляет собой непереобученную модель YAMNet, а laba_1NNtrain является уже переобученной моделью для определения классов cat и dog
## Запуск кода:
Скачайте файл **laba1_NNtrain.ipynb** и запустите его с использованием python-ноутбука ([Google Colab](https://colab.research.google.com/)).

Или можете открыть его сразу в Colab:
<br><br>
<a target="_blank" href="https://colab.research.google.com/github/meeFp/Laba1_NN/blob/main/laba1_NNtrain.ipynb">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/>
</a>

## Результаты:
- Обнаружение нового класса собака
  [lay-sobaki.webm](https://github.com/meeFp/Laba1_NN/assets/119287468/5f016740-6d19-4588-8aa0-95c385bfe39b)

  ![image](https://github.com/meeFp/Laba1_NN/assets/119287468/626c9601-0cf3-4d78-8b39-ec270a68b96a)
  
  ![image](https://github.com/meeFp/Laba1_NN/assets/119287468/492f0507-4023-4a90-a8ed-460905b00ebc)
 
- Обнаружение нового класса кот
  [cat.webm](https://github.com/meeFp/Laba1_NN/assets/119287468/7305634e-7d2f-4ce1-896b-b344c3e783e2)

  ![image](https://github.com/meeFp/Laba1_NN/assets/119287468/b3b467a9-d98e-4f57-9817-ee0ebe4558ad)

  ![image](https://github.com/meeFp/Laba1_NN/assets/119287468/be936584-f355-4584-a24d-52e11490fbe2)

- Обнаружение старого класса телефонный звонок
  [klassicheskiy-zvonok-telefona-33191.webm](https://github.com/meeFp/Laba1_NN/assets/119287468/1897180b-2710-4930-a687-d33f85acf455)

  ![image](https://github.com/meeFp/Laba1_NN/assets/119287468/31c7532b-322a-4616-a868-cbead7f29af4)

  ![image](https://github.com/meeFp/Laba1_NN/assets/119287468/204479f2-37f4-46ba-bcfa-d5efaf8d6741)

После обучения модели и её тестирования мы успешно достигли точности классификации для звуковых сигналов собак и кошек. Полученные результаты демонстрируют эффективность разработанной модели в автоматическом выделении и классификации звуковых сигналов.


