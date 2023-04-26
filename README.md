# За тимот ESS:

Проект на: [Симон Анастасов 201003](https://simonanastasov.netlify.app), [Давид Ѓорѓиевски 203018](https://the-david-gorgievski-3-0.vercel.app/), [Глигорчо Глигоров 203125](https://gligorcogligorov.github.io/GligorcoGligorov/index.html)

Изработен во рамки на Финки, за предметот Визуелно Програмирање, воден од Дејан Ѓорѓевиќ и Стефан Андонов.

Изработен на: 2.7.2022г.

# Функционалности на играта:

Ние креиравме полу-реплика на играта Тенк Трабл (оригиналната игра, која исто така е многу забавна, е достапна на линкот https://tanktrouble.com).

Се разбира, нашата игра е кодирана од нула, и единствено од нас. (И неколку добри луѓе што одговориле на прашања на Stack Overflow во 2012 година 😜).

## Цел на играта:

Играта се игра со 2 играчи (2 Тенка). Тие се движат низ лавиринт, при што паметно треба да ги искористат ѕидовите за да се скријат од куршумите на непријателскиот тенк, а притоа да успеат да го погодат непријателскиот тенк со своите куршуми. Еве како изгледа тоа (без и со испукани куршуми):

![An example of a level of the game](https://github.com/SimonAnastasov/TankTroublESS/blob/master/ReadmeImages/Level.png?raw=true)

![An example of a level of the game with bullets](https://github.com/SimonAnastasov/TankTroublESS/blob/master/ReadmeImages/Bullets.png?raw=true)

## Контролирање на тенковите:

Зелениот тенк се движи на копчињата 'WASD' и пука на копчето 'Q'. Црвениот тенк се движи на 'стрелките' и пука на 'SPACE'.
На следната слика ова е прикажано визуелно.

![Controlling the tanks movement](https://github.com/SimonAnastasov/TankTroublESS/blob/master/ReadmeImages/Controls.png?raw=true)

## Дополнителни работи што ги има во играта:

### - Форма за помош:

![Controlling the tanks movement](https://github.com/SimonAnastasov/TankTroublESS/blob/master/ReadmeImages/HowToPlay.png?raw=true)

### - Секција „За Нас“:

![Controlling the tanks movement](https://github.com/SimonAnastasov/TankTroublESS/blob/master/ReadmeImages/AboutUs.png?raw=true)

### - Статус стрип (долу лево, види ја првата слика погоре), кој го покажува резултатот.

# Кодирање на играта:

## Структури:

Играта е базирана на класи и интеракција помеѓу објекти од класите. Некои од класите кои ги имаме се: PlayingField, Background, Walls, Tank, Bullet...

Во класите се чуваат информации како: X и Y координатата на објектот кој класата го претставува, Должината и висината на објектот, во некои од класите има и листи од објекти (пример листа од куршуми во класата тенк), а во некои има и параметри како што се време до исчезнување (пример класата за куршум).

## Мултимедиа:

Користиме слики и аудио, со цел да го подобриме квалитетот на играта и да го зголемиме задоволството кај играчите.

## Објаснување на една интересна функција:

![Controlling the tanks movement](https://github.com/SimonAnastasov/TankTroublESS/blob/master/ReadmeImages/Function.png?raw=true)

Ова е функцијата Draw во класта Tank.

---

Интересно е што во C# Windows Forms нема едноставна функција за ротирање на објект. А, без ротирање, нашата игра не би можела да се игра.

Најпрво функцијата SetTankBox() едноставно ги поставува X и Y координатите, како и Ротацијата на тенкот (но, ги поставува како параметри кои подолу треба да ги обработиме). 

Функцијата CalculateWidthAndHeight() ја пресметува должината и висината на квадратот околу сликата на тенкот по неговото ротирање, бидејќи таа се менува. Во оваа функција има многу математика и не е лесна за следење, па затоа не поставивме слика од неа.

---

Сега во продолжение, ќе го објасниме кодот што следи, од горната слика. Најпрво креираме бит-мапа со димензии кои претходно ги пресметавме (ќе ги викаме ротирани димензии), и креираме поле со графика базирано на таа бит-мапа.

Потоа, оваа графика ја поместуваме надесно и надолу за вредност еднаква на половина од овие ротирани димензии, па ја вршиме ротацијата преку трансформација на бит-мапата, и ја враќаме графиката налево и нагоре за половина од оригиналните димензии (на неротиран тенк).

Потоа, го цртаме тенкот на позиција (0, 0) од својата засебна графика (Ова не е исто со позицијата (0, 0) на целата апликација!).

На крај, ја поместуваме целата графика на целата апликација, со цел тенкот навистина да биде исцртан на посакуваните X и Y координати, и доколку тенкот се уште е жив, го прикажуваме на екран.

Забелешка: Сите претходни чекори мора да ги направиме и кога не е жив тенкот, поради начинот на кој работат овие релативни графики на тенковите.

# За крај:

Ви благодариме на вниманието и уживајте во играта 🥰.