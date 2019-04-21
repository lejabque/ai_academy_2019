![](https://habrastorage.org/webt/35/br/pa/35brpa1ufsycwqxpb58ikycpxs4.jpeg)
# AI Academy Dota2 Skill Prediction
*AI-Academy* - проект Сбербанка, направленный на популяризацию образования в сфере искусственного интеллекта среди школьников. В рамках проекта проходил хакатон, в рамаах которого участникам предлагалось решить задачу оценки квалификации игрока в Dota 2 по данным его матчей.

Материалы к [соревнованию по определению опытного игрока Dota2](https://contest.ai-academy.ru/competition)

**Здесь представлено моё решение, которое заняло 2 место на финальном этапе с точностью 0.91250.**
## Описание задачи

В игре Dota 2 участвуют две стороны: команды сил Света (The Radiant) и сил Тьмы (The Dire). Каждая команда состоит из 5 игроков — персонажей со своими уникальными способностями. Перед началом матча каждый игрок выбирает себе одного героя из 116 возможных. Цель игры — разрушить трон, находящийся на базе противника.

Повышая игровые навыки, игроки повышают свой рейтинг и получают медали опыта. Эксперты по игре Dota 2 утверждают, что легко могут отличить матч новичка от игры опытного игрока.

**Задача — построить алгоритм, который сможет определять опытность игрока по статистике из одного матча.**

## Формат набора данных

Для решения задачи участникам предоставляется набор из почти 50000 примеров матчей, уровень игрока в которых известен. Для каждого из ≈21000 тестовых примеров, участникам необходимо проанализировать данные о матче при помощи своих алгоритмов и дать ответ — опытный ли был игрок.

Участникам предоставляются наборы данных с примерами матчей. Каждый пример описывает характеристики матча и статистику одного из игроков на момент окончания матча. Все примеры имеют уникальный идентификатор "id".

Всего два набора:

1. Обучающий (train), в котором для каждого примера известен класс игрока.
2. Тестовый (test), для которых участникам неизвестна опытность игрока — ее необходимо вычислить.

Наборы данных содержатся в `data/data_zip.zip`.

Описание полей с данными можно найти в Jupyter-нотбуках.

## Формат решения

Для каждого примера из тестового набора необходимо предсказать опытность игрока. В систему необходимо предоставить для проверки CSV-таблицу с предсказаниями, она должна содержать две колонки: `id` — идентификатор примера, `skilled_prob` - вероятность принадлежности игрока к классу "Skilled".

## Оценка качества

Качество решения оценивается с помощью метрики ROC-AUC.

## Материалы к задаче

- [материалы](https://contest.ai-academy.ru/competition) Академии Искусственного Интеллекта Сбебанка;
- разбор [похожих задач](https://www.youtube.com/watch?v=YSQqHlQwQDY&t=50s) на [тренировках по машинному обучению](https://www.youtube.com/channel/UCeq6ZIlvC9SVsfhfKnSvM9w).

Для решения использован язык программирования Python, так как для него есть большое число библиотек для анализа данных: NumPy, Pandas, SciKit-Learn и другие. В качестве инструмента разработки — интерактивная среда Jupyter, в качестве основных моделей - CatBoost и LightGBM.

Базовый пример решения от организаторов доступен в виде Jupyter-тетради: [baseline/Dota2SkillPrediction_Tutorial.ipynb](https://github.com/datasouls/competition-ai-academy-2019/blob/master/Dota2SkillPrediction_Tutorial.ipynb)



