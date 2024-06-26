# Багатошаровий персептрон. Розпізнавання геометричних фігур

Персептрон являє з себе найпростішу нейронну мережу, відповідно потребує
три базові компоненти для своєї роботи:
1. Декілька шарів нейронів
    В нашому випадку ми маємо базовий багатошаровий персептрон, що
    складається з 3-х шарів: вхідний, прихований та вихідний.
2. Навчаюча множина
    Навчаюча множина генерується програмно. Випадковим чином
    вибираються точки у прямокутному зображенні заданого розміру та
    формують геометричну фігуру. В нашому випадку це трикутник,
    прямокутник та лінія.
3. Алгоритм корекції помилки
    Використаний класичний алгоритм зворотного поширення помилки
    (backpropagation), що зустрічається у більшості простий нейронних
    мереж.

Також слід перерахувати кілька важливих характеристик розробленої нами
нейронної мережі:
1. Функція активації

    Використовується стандартна функція – сигмоїд

    ![Знімок екрана 2024-04-05 101143](https://github.com/logovaser/Shape-NN-2016/assets/11948273/6f666bba-c5f7-4cf5-b92a-5a0bc73068a0)

    Де α = 1
2. Функція градієнту

    Для вихідного шару
    
    ![Знімок екрана 2024-04-05 101209](https://github.com/logovaser/Shape-NN-2016/assets/11948273/8b3911a1-b77c-4605-9ddd-4892ad002f33)

    Де:
    * OUT – вихід нейрона
    * T – очікувана вихідна величина
    * δ – просто змінна, що тримає в собі коефіцієнт. Використовується
    для корекції ваги як у поточному шарі, так і в наступному
    
    Для прихованих шарів
    
    ![Знімок екрана 2024-04-05 101242](https://github.com/logovaser/Shape-NN-2016/assets/11948273/22c0bffa-fea1-44e8-8400-e1731948424c)

    Де:
    * ω – вага зв’язку між двома нейронами (поточного та попереднього
    шару)
    * n – номер поточного шару
    * i – ітератор
    
    Нарешті:
    
    ![Знімок екрана 2024-04-05 101302](https://github.com/logovaser/Shape-NN-2016/assets/11948273/57266c49-3d74-4568-9084-e1667f501d30)

3. Вхідний шар
    Зображення перетворюється у двовимірний масив з нулів та одиниць
    розмірністю 20х20 для зручнішої візуалізації у консолі. Навчаюча
    множина відразу формується у цьому вигляді.
    Для того, щоб подати дані на вхід, масив перетворюється з
    двовимірного у одновимірний.
    У приведеній програмі вхідний шар містить 400 нейронів (20*20)
4. Прихований шар
    Складається з 50-ти нейронів
5. Вихідний шар
    3 нейрона. 1 – трикутник, 2 – прямокутник, 3 – лінія.
6. Коефіцієнт навчання
    Підлаштовується динамічно, початкове значення – 0.1. Під час
    навчання, якщо значення помилки залишається менше заданого рівня,
    коефіцієнт трохи зменшується. Це дозволяє точніше налаштувати ваги.

Код написаний на мові Javascript ES6
Перше завантаження (навчання нейронної мережі) може тривати кілька хвилин, але розпізнавання працює
миттєво.
