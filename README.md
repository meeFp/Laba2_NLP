# **Использование глубоких нейронных сетей для синтеза текста: анализ эффективности в создании естественно звучащих текстов.**
## Описание
### Цель:
Использовать глубокие нейросети модель для синтеза текста: анализ эффективности в создании естественно звучащих текстов.
### О проекте:
Этот проект демонстрирует использование библиотеки Tortoise TTS([Tortoise TTS](https://github.com/jnordberg/tortoise-tts)) для синтеза речи на основе глубоких нейронных сетей. В проекте используется модель Tortoise([Tortoise](https://huggingface.co/ken2ki/tortoise)) и предоставляется пример работы с пользовательским голосом. В данной работе использовался мой собственный голос, как датасэт(Голос.zip([Госол.zip](https://github.com/meeFp/Laba2_NLP/blob/main/Голоса.zip)))


## Используемые библиотеки

- scipy
- transformers
- einops
- rotary-embedding-torch
- unidecode
- torch
- trochaudio
- tortoise.api
- tortoise.utils.audio

## Инструкции по установке:
1. Скачайте датасет Голос.zip([Госол.zip](https://github.com/meeFp/Laba2_NLP/blob/main/Голоса.zip)) или же создайте свой датасет с помощью сторонних программ, например, я использовал для записи своего голоса прогамму Audacity([Audacity](https://www.audacityteam.org/download/?ref=henrywithu.com)). В данной программе очень удобный интерфейс
2.  Установите необходимые библиотеки, выполнив следующие команды:
     ```python
    !pip3 install -U scipy
    !git clone https://github.com/jnordberg/tortoise-tts.git
    %cd tortoise-tts
    !pip3 install transformers==4.19.0
    !pip3 install -r requirements.txt
    !python3 setup.py install
    !pip install einops==0.3.0
    !pip install rotary-embedding-torch==0.2.2
    !pip install unidecode==1.2.0
    ```

    ```python
    import torch
    import torchaudio
    import torch.nn as nn
    import torch.nn.functional as F

    import IPython

    from tortoise.api import TextToSpeech
    from tortoise.utils.audio import load_audio, load_voice, load_voices
    ```

3. В данной строчке генерируем текст, который в дальнейшем превратиться в аудиоинтепретацию
   ```python
   # Это текст, который будет произнесен.
     text = "Витя, братан! Погода сегодня хорошая. Какие у тебя планы на выходные? Пойдем в кино?»"

     # Выберите «предустановленный режим» для определения качества. Опции: {"ultra_fast", "fast" (по умолчанию), "standard", "high_quality"}.
     preset = "fast"
   ```

4. После того как вы скачали датасет или же создали свой и добрались до данного этапа можете загрузить файлы формата wav и обязятельно введите новый **CUSTOM_VOICE_NAME**. 
   
   ![DkXvHD183Z0](https://github.com/meeFp/Laba2_NLP/assets/119287468/3a9693b2-9e54-4997-b2b9-f804b9e66303)


## Примечательные особенности:
- Проект основан на библиотеке Tortoise TTS, которая предоставляет удобный интерфейс для синтеза речи с использованием глубоких нейронных сетей
- Данный проект взаимодействует с хабом HuggingFace для загрузки моделей, что обеспечивает доступ к различным предобученным генеративным моделям.
- Проект демонстрирует возможность использования собственного голоса для синтеза речи. Это позволяет создавать персонализированные голоса для конкретных приложений.
- Реализован выбор уровня качества при синтезе речи с помощью предустановленных режимов: "ultra_fast", "fast", "standard", "high_quality".
- Результаты синтеза речи сохраняются в аудиофайл, который легко прослушать и визуализировать, что обеспечивает наглядное представление полученных результатов.
## Запуск кода:
Скачайте файл **laba2_NLP.ipynb** и запустите его с использованием python-ноутбука ([Google Colab](https://colab.research.google.com/)).

Или можете открыть его сразу в Colab:
<br><br>
<a target="_blank" href="https://colab.research.google.com/github/meeFp/Laba2_NLP/blob/main/laba2_NLP_.ipynb">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/>
</a>

## Результаты:
- Синтез текста при 3 аудифайлах

   ![result3](https://github.com/meeFp/Laba2_NLP/assets/119287468/b2c34c42-cdf0-4503-9684-22a189adf440)
  
   [reusult_for_3examples.webm](https://github.com/meeFp/Laba2_NLP/assets/119287468/21d149d3-4231-4897-add8-2887c38d35ef)
 
- Обнаружение нового класса кот
  [cat.webm](https://github.com/meeFp/Laba1_NN/assets/119287468/7305634e-7d2f-4ce1-896b-b344c3e783e2)

  ![image](https://github.com/meeFp/Laba1_NN/assets/119287468/b3b467a9-d98e-4f57-9817-ee0ebe4558ad)

  ![image](https://github.com/meeFp/Laba1_NN/assets/119287468/be936584-f355-4584-a24d-52e11490fbe2)

- Обнаружение старого класса телефонный звонок
  [klassicheskiy-zvonok-telefona-33191.webm](https://github.com/meeFp/Laba1_NN/assets/119287468/1897180b-2710-4930-a687-d33f85acf455)

  ![image](https://github.com/meeFp/Laba1_NN/assets/119287468/31c7532b-322a-4616-a868-cbead7f29af4)

  ![image](https://github.com/meeFp/Laba1_NN/assets/119287468/204479f2-37f4-46ba-bcfa-d5efaf8d6741)

После обучения модели и её тестирования мы успешно достигли точности классификации для звуковых сигналов собак и кошек. Полученные результаты демонстрируют эффективность разработанной модели в автоматическом выделении и классификации звуковых сигналов.


