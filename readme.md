# Заметки по THREE.js

## Содержание
* [Вступление](#вступление)
  * [Проект WEBVKUBE. Первый бесплатный курс на youtube](#проект-webvkube-первый-бесплатный-курс-на-youtube)
    * [Урок 1. Введение](#урок-1-введение)
    * [Урок 2. Модули, импорт, экспорт](#урок-2-модули-импорт-экспорт)
      * [Экспорт и импорт](#экспорт-и-импорт)
      * [Подключение модулей и вызов на странице](#подключение-модулей-и-вызов-на-странице)
    * [Урок 3. Создаем простую сцену](#урок-3-создаем-простую-сцену)
    * [Урок 4. Объект3D, его параметры и методы](#урок-4-объект3d-его-параметры-и-методы)
    * [Урок 5. Перемещение и векторы](#урок-5-перемещение-и-векторы)
    * [Урок 6. Поворот объектов](#урок-6-поворот-объектов)
* [Документация](#документация)
  * [Объекты в целом](#объекты-в-целом)
  * [Меш](#меш)
    * [Геометрия](#геометрия)
    * [Материал](#материал)
  * [Сцена](#сцена)
  * [Камера](#камера)
  * [Свет](#свет)
  * [Вектор](#вектор)
  * [Эйлер](#эйлер)
  * [Кватернион](#кватернион)
  * [Рендер](#рендер)

## Вступление
[Вернуться к содержанию][toc]

Изначально в данном документе были заметки по бесплатному курсу по THREE.js от [webvkube]. Но позже я решил добавить информацию и по другим материалам. Еще есть заметки/перевод документации. Перевод вольный, сверяйте все с официальной документацией.  

К бесплатному курсу был ограничен доступ. Ссылки оставлю на всякий случай. Если что - все вопросы в группу автора. Материал очень крутой! :thumbsup:

##### VS Code Intellisense для THREE.js

Я использую VS Code и Intellisense для библиотеки THREE.js заработал автоматически после импорта библиотеки. Но на всякий случай могу предложить почитать [здесь][vscode_intellisense] как сделать себе в редакторе Intellisense для THREE.js, если вдруг автоматически не заработал.

### Проект WEBVKUBE. Первый бесплатный курс на youtube
[Вернуться к содержанию][toc]

* [Канал][youtube_main_channel] уроков на Youtube.
* [Группа ВК][vk_kurspothreejs] 

Список уроков начального бесплатного курса на Youtube :
* Урок 01. [Введение.](https://www.youtube.com/watch?v=DRiVzLca3xc)
* Урок 02. [Модули, импорт, экспорт.](https://www.youtube.com/watch?v=scAiW8rzvLc)
* Урок 03. [Создаем простую сцену.](https://www.youtube.com/watch?v=ECAYu1mZUzM)
* Урок 04. [Объект3D, его параметры и методы.](https://www.youtube.com/watch?v=dADyZorNysU)
* Урок 05. [Перемещение и векторы.](https://www.youtube.com/watch?v=MJUOLZyI7iE)
* Урок 06. [Поворот объектов.](https://www.youtube.com/watch?v=NYqh5flYKEo)
* Урок 07. [Геометрия объекта.](https://www.youtube.com/watch?v=lm7uXWyziFs)
* Урок 08. [Материалы.](https://www.youtube.com/watch?v=aOkmujuzO2M)
* Урок 09. [Текстуры, свет, камеры.](https://www.youtube.com/watch?v=0FW3kyuRyyw)
* Урок 10. [Ресайз, Взаимодействие с объектом.](https://www.youtube.com/watch?v=yHQugrtmkH4)
* Урок 11. [Создаем платформер часть 1.](https://www.youtube.com/watch?v=gXwsuVicjV4)
* Урок 12. [Состояния. Создаем платформер часть 2.](https://www.youtube.com/watch?v=ap2Y3G6RE0c)
* Урок 13. [Создаем платформер часть 3. ИИ Проверка нанесения урона.](https://www.youtube.com/watch?v=y5ZlQeQOtAg)

#### Урок 1. Введение
[Вернуться к содержанию][toc]

Официальный сайт проекта [THREE.js][three_js_site].

Скачать библиотеку three.js с [GitHub][three_js_github_build].

#### Урок 2. Модули, импорт, экспорт
[Вернуться к содержанию][toc]

Лучше организовать код и работу с ним через модули.

##### Экспорт и импорт
[Вернуться к содержанию][toc]

* Если **в файле только один класс, объект или переменная**, то экспорт можно делать через слово `default`, а при импорте просто указываем переменную, куда складываем импортированные данные.

```javascript
// ./js/data.js

export default 1; // например, экспортируем просто число

// или
export default class{}; // может быть класс

// или
export default {}; // может быть объект
```

```javascript
// ./js/app.js

import a from './js/data.js';
alert(a);
export default true;
```

* Если **в файле несколько переменных, объектов или классов**, то надо их сначала объявить, потом через { } экспортировать. При импорте тоже нужно указать фигурные скобки { }.

```javascript
// ./js/data.js

let a = 1;
export {a};
```

```javascript
// ./js/app.js

import {a} from './js/data.js';
alert(a);
export default true;
```

* Если **экспортируем несколько переменных**, указываем их через запятую , . Импортируем также через через запятую , .

```javascript
// ./js/data.js

let a = 1;
let b = 3:
export {a, b};
```

```javascript
// ./js/app.js

import {a, b} from './js/data.js';
alert(a);
alert(b);
export default true;
```

* Если нужно **экспортировать все**, то указываем через `* as` и указываем имя родителя.

```javascript
// ./js/app.js

import * as data from './js/data.js';
alert(data.a);
alert(data.b);
export default true;
```

* Иногда модули нужны только **для объединения других модулей** модулей. Тогда вместо `import` пишем `export`, а импорт также делам через `* as`.

```javascript
// ./js/data.js

let a = 1;
let b = 3:
export {a, b};
```

```javascript
// ./js/app.js

export * from './js/data.js'; // в данном случае файл является передаточным звеном
```

```html
<!-- ./index.html -->

<script type="module">
  import * as app from './js/app.js';
  console.log(app.a, app.b); 
</script>
``` 

* Также, **для объединении нескольких файлов** нужно просто их добавить.

```javascript
// ./js/app.js

export * from './js/data.js';
export * from './js/data1.js';
export * from './js/data2.js';
export * from './js/data3.js';
// и т.д.
```

##### Подключение модулей и вызов на странице
[Вернуться к содержанию][toc]

* **Подключение приложения** в текущем подходе осуществляется в index.html:

```html
<!-- ./index.html -->

<script type="module">
  import app from './js/app.js';
</script>
``` 

В данном случае, `app` может быть любым другим словом.

#### Урок 3. Создаем простую сцену
[Вернуться к содержанию][toc]

Все 3d базируется на нескольких понятиях, о которых нужно помнить при создании приложения. Это:
1. Объект:
    * Геометрия;
    * Материал.
2. Сцена.
3. Камера.
4. Свет.
5. Рендер.

Модуль приложения описан в файле app.js. Пока что там экспортируются только 2 дефолтные функции: **init** для инициализации проекта и **update** для постоянной прорисовки (рендера) картинки. В index.html этот модуль подключается и там же вызывается инициализация приложения. Обрати внимание на то, что <span id="lesson-3-renderer-recursion-update-function">рекурсивная функция рендерера update</span> построена так: в ней сначала запоминается контекст выполнения функции, который нам нужен, а только потом будет рекурсия нашего контекста. Это в данном примере так. Дальше посмотрим, может что поменяется. Дополнительно в index.html для body задаются отступы 0 и overflow: hidden, т.к. почему-то вылезает скролбар все время. Возможно, у других это не так.

```html
<!-- index.html -->

<style>
  body {
    margin: 0;
    overflow: hidden;
  }
</style>

<script type="module">
  import app from './js/app.js';
  app.init();
</script>
```

```javascript
// app.js

export default {

  // функция инициализации приложения
  init: function () {
    // тут объявляются все объекты, сцены, камеры, свет и т.д.
    this.update();
  },

  // функция прорисовки (обновления картинки)
  update: function () {
    let that = this; // здесь сохранили контекст выполнения
    this.renderer.render(this.scene, this.camera); // запустили рендерер
    requestAnimationFrame( function () {
      that.update();
    }); // рекурсивно вызвали функцию обновления
  }
};
```

#### Урок 4. Объект3D, его параметры и методы
[Вернуться к содержанию][toc]

Объекты можно добавлять друг в друга. Тогда создается иерархия объектов: родитель -> потомок. И если, например, двигать родителя, то потомок тоже будет двигаться.

Задавать цвет стандартного материала (наверное, и не только) можно через метод `.setHex()`, например, `obj.material.color.setHex(0xff00bb).

Отличие функции `.clone()` от `.copy()` в том, что когда мы копируем, то 2й объект уже создан. 

#### Урок 5. Перемещение и векторы
[Вернуться к содержанию][toc]

Векторы отвечают за направление. Обычно направление задано нормальизованным вектором (т.е. его длина равна 1). Для перемещения нормализованный вектор умножают на скорость.  

**Чтобы направить** объект2 **следовать за другим** объектом1, нужно:
1. Находить постоянно вектор-разницу между о1 и о2 - `.subVectors()`.
2. Задавать постоянно длину найденного вектора (или нормализовать и умножить на скорость).
3. Добавлять постоянно все время к позиции о2 полученный вектор.

`.position.distanceTo()` **лучше не применять**, если в сцене много объектов. Это ресурсозатаратно, т.к. в каждой операции считается извлечение корня. Дистанция до объекта находится как корень квадратный из суммы квадратов проекций по осям x и y от объекта до объекта. Т.е. по теореме Пифагора. Более **быстрая версия этой функции** - функция `.position.distanceToSquared()`. Она не извлекает корень при расчете дистанции.

Т.к. многие методы у векторов возвращают тоже вектор, то можно писать сложные последовательные констркуции через точку, типа `vec1.add(vec2.position).multiplyScalar(2).normilize();` и т.д.

**Чтобы вращать** объект2 **вокруг другого** объекта1, нужно:
1. Раз определить угол = 0.
2. Постоянно изменять угол на какую-то величину.
3. Задавать постоянно позицию объекта2 по x = 0 + N * Math.cos(угол). 
4. Задавать постоянно позицию объекта2 по y = 0 + N * Math.sin(угол).
Здесь N - это расстояние от объекта1 до объекта2.

**Один из вариантов выполнения ДЗ.** Мое первое решение. Делаем сферы и куб. Куб ставим на сферу. В апдейте пишем: Если дистанция от сферы до куба меньше 0.01, то вектор направления = вектор сферы 2 - вектор сферы 1. И так для каждоый сферы. А после условия устанавливаем длину вектора и добавляем его к позиции куба.

#### Урок 6. Поворот объектов
[Вернуться к содержанию][toc]

А вот и **решение предыдущей задачи** из Урока 5. Я был близок к пониманию :smile:

1. Делаем массив сфер.
2. Заполняем его сферами.
3. В цикле задаем каждой сфере произвольное положение, добавляем сферу в сцену, добавляем сферу в массив.
4. Присваиваем переменной 1й объект массива.
5. Делам счетчик, в котором храним номер сферы.
6. В апдейте находим направление как разницу векторов текущего элемента массива сфер и куба. Задаем ему тут же длину. Прибавляем вектор к положению куба.
7. Потом проверка: если дистанция от куба до текущего элемента массива сфер меньше половины направления, то счетчик увеличивается на 1. И если счетчик дошел больше длины массива со сферами, то счетчик сбрасывается на 0.

Единственное помни, что проверять достижение нужной координаты через ориентирование на дистанцию в половину меньше направления, не совсем верно. Это верно только когда путь, который нужно пройти, больше длины вектора направления (включая скорость). Так что всегда проверять надо этот момент.







## Документация
[Вернуться к содержанию][toc]

Здесь коротко собираю информацию, чтобы не забыть про объекты, параметры функций, варианты и т.д.

[Офиициальная документация][three_js_doc_site] по THREE.js

### Объекты в целом
[Вернуться к содержанию][toc]

Вообще-то, объектом может быть все в приложении: меш, камера, источник света, сцена. В свою очередь меш это объект, который состоит из геометрии и материала.

Все объекты наследуются от класса `Object3D`.

* **Object3D**

Можем создать пустой объект (болванку), для помещения в нее других объектов

```javascript
let someObj = new THREE.Object3D();
```

**Cвойства**

```javascript
// Вложенные объекты / массив с потомками (Array)
.children;

// Номер объекта (Integer, def: empty) 
.id;

// Имя объекта (String)
.name;

// Родитель / ссылка на объект по иерархии выше
.parent;

// Позиция и варианты как ее задать (positiob - это Vector3, запомни!)
.position.x; // а также .y и .z
.position.set(x, y, z); // задается сразу 3 координаты
.position.add(Vector3);

// Поворот (Quaternion). См. раздел по кватернионам дополнительно
.quaternion;

// Поворот (Euler)
.rotation.x; // а также .y и .z (в радианах)

// Масштаб (Vector3)
.scale.x; // а также .y и .z

// Видимость объекта в сцене (Boolean, def: true)
.visible;
```

**Методы**

```javascript
// Добавить объект в объект
.add(Object);

// Отбрасывать тени (Boolean, def: false)
.castShadow();

// Клонировать объект (геометрия и материал остаются прежними)
// Также, можно клонировать материал, например
.clone()
// ex
cube1 = cube2.clone();  

// Копирование объектов. Копирует информацию с другоого объекта
.copy(Object);

// Поиск объекта по id
.getObjectById(Integer)

// Поиск объекта по имени
.getObjectByName(String)

// Поворот объекта на определенную точку или другой объект
.lookAt(x, y, z);
// ex
camera.lookAt(cube.position);
camera.lookAt(1, 5, 3);

// Удалить объект из объекта
.remove(Object);

// Перемещение относительно локальных координат объекта
.translateX(Float);
.translateY(Float);
.translateZ(Float);
```

### Меш
[Вернуться к содержанию][toc]

Наследуется от `Object3D`.

* **Меш**

Меш включает в себя геометрию и материал. Это то, что мы увидим как объект в сцене. Например, стул, дерево, мяч и т.д. - все это будут мэши со свое геометрией и материалами.

```javascript
let mesh = new THREE.Mesh(геометрия, материал);
```

#### Геометрия
[Вернуться к содержанию][toc]

* **Куб**

Может быть неравносторонним. Размеры в числах. Принимаем, что 1 = 1 м.

```javascript
let boxGeometry = new THREE.BoxGeometry(ширина, высота, глубина);
```

* **Сфера**

Размеры в числах. 

```javascript
let sphereGeometry = new THREE.SphereGeometry(радиус, кол-во ребер по горизонтали, кол-во ребер по вертикали);
```

#### Материал
[Вернуться к содержанию][toc]

* **Стандартный материал**

Просто покрывает мэш в заданный цвет. В параметр материала передаются свойства в виде объекта { }. Задаются свойства цвета, шераховатости, прозрачности, металлизированности, карты нормалей, AO и т.д. Формат цвета `0x000000` - последние 6 цифр это RRGGBB в 16-ричной системе счисления от 0 до f.

<!-- TODO добавь описание параметров -->
```javascript
let materialStandart = new THREE.MeshStandartMaterial({
  color: 0x000000,
  wireframe: false, // def: false
  // ....
});

// Менять свойства можем так:
someObj.material.color.setHex(0x000000);
```

### Сцена
[Вернуться к содержанию][toc]

* **Сцена**

Наследуется от `Object3D`.

Сцена как коробка, в которую складывают все объекты и в которой разворачиваются все действия. Перед запуском отрисовки (рендером), надо поместить все объекты, включая меши, свет, камеры. Без добавления в сцену объектов они просто не будут отрисовываться.

```javascript
let scene = new THREE.Scene();

// добавляем в сцену объекты
scene.add(перечисляем что добавляем);
```

### Камера
[Вернуться к содержанию][toc]

Наследуется от `Object3D`.

* **Перспективная** камера

Наследуется от `Object3D -> Camera`.

Показывает картинку с учетом перспективы. Так можно понять глубину картинки. Объекты при приближении и удалении меняют размер. Есть перспектива. Понятно, да? :wink: В параметры передаем угол обзора (FOV, field of view) бери 60 или 75 для начала; отношение сторон для отображения бери window.innerWidth / window.innerHeight; ближнюю границу клиппинга бери 0.1; дальнюю границу клиппинга бери 100 для начала.

```javascript
let cameraPersp = new THREE.PerspectiveCamera(угол обзора, 
  отншение сторон для отображения, 
  ближняя граница прорисовки, 
  дальняя граница прорисовки);
```

* **Ортографическая** камера

Наследуется от `Object3D -> Camera`.

Это для отображения плоских сцен. 2d, например. Здесь не будет видно перспективы. Объекты на разном расстоянии будут одинакового размера.
<!-- TODO опиши параметры ортографической камеры и какие для начала брать значения -->

```javascript
let cameraOrto = new THREE.OrtographicCamera();
```

### Свет
[Вернуться к содержанию][toc] 

Наследуется от `Object3D`.

* **Гемисферический** источник света.

Наследуется от `Object3D -> Light`.

Свет будет подаваться сверху и снизу. Цвета верхнего и нижнего света в формате `0x000000`; интенсивность в числах бери 1 для начала.

```javascript
let lightHemi = new THREE.HemisphereLight(цвет верхнего света, цвет нижнего света, интенсивность источника света) 
```

### Вектор
[Вернуться к содержанию][toc]

Это про направления.

* **Vector3**

Это трехмерный вектор с координатами x, y, z. При создании можем сразу указать координаты x, y, z (def: 0, 0, 0). Но это не обязательно.

```javascript
let direction = new THREE.Vector3d();
```

**Свойства**

Координаты x, y, z.

```javascript
.x // или .y или .z
```

**Методы**

```javascript
// Добавить вектор
.add(Vector3);

// Добавить число к координате
.addScalar();

// Сложить два вектора. 
.addVectors(вектор1, вектор2)

// Клонировать - создает новый вектор на основе другого
.clone();

// Копирует данные - копирует в уже сущетвующий вектор данные другого
.copy(Vector3);

// Деление вектора
.divide(Vector3); 

// Деление вектора на число
.divideScalar();

// Узнать дистанцию до объекта (посмтри пример в уроке 5 - в блоке if сравнение)
.distanceTo(Vector3);

// Узнать дистанцию до объекта (в квадрате) - нужна для более быстрой работы,
// чем distancTo(), т.к. не вычисляет квадратный корень,
// т.е. нужна только для сравнения / поиска расстояния между объектами
.distanceToSquared();

// Узнать длину вектора
.length();

// Узнать длину вектора в квадрате
.lengthSq();

// Умножение вектора на вектор
.multiply(Vector3);

// Умножение вектора на число 
.multiplyScalar(Float);

// Умножение векторов
.multiplyVectors(Vector3, Vector3);

// Нормирование вектора
.normilize();

// Задать позицию вектора, в числах
.set(x, y, z);

// Задать длину вектора
.setLength(Float);

// Вычитание вектора из вектора
.sub(Vector3);

// Вычитание числа из координат вектора
.subScalar(Float);

// Вычитание двух векторов в переменную (вектор). Оба параметра: Vector3.
.subVectors(уменьшаемое, вычитаемое);
```

### Эйлер
[Вернуться к содержанию][toc]

Нужен для поворотов - это просто поворот вокруг оси x, y или z.
При создании указываем на сколько повернуть по каждой из осей и 4й параметр - порядок осей при повороте (очень важно это. Пишется большими буквами).

```javascript
let eul = new THREE.Euler(x, y, z, 'XYZ');
```

**Свойства**

```javascript
// Задает порядок осей для поворота ('XYZ')
.order;
```

**Методы**

```javascript
// Клонирование эйлера
.clone();

// Копирование эйлера
.copy(другой эйлер);

// Переопределение поряка поворота по осям (как .order, только .reorder лол:)).
// Тут смысл в том, что может быть большая цепочка действий черзе точку. Вот тут этот метод и пригодится.
.reorder(новый порядок)

// Задать эйлер
.set(x, y, z, порядок);
```

### Кватернион
[Вернуться к содержанию][toc]

Это лютая дичь, которая нужна для поворота объектов вокруг заданной оси и заданноу углу.

**Свойства**


**Методы**

```javascript
// Поворот вокруг указанной оси (Vector3) на определенный угол в радианах (Float)
.setFromAxisAngle(ось, угол поворота вокруг оси)
```


### Рендер
[Вернуться к содержанию][toc]

Рендер. Рендерер. Прорисовыватель всего того, что ты построил. Делает картинку. Для статичной картинки его можно вызвать один раз. Для работы приложения его нужно вызывать каждый кадр, т.е. чтобы каждый кадр перерисовывалась сцена. Обычно это 60 кадров в секунду (60 fps). Тогда рендерер помещают либо в таймер, либо в рекурсивную функцию. 

* **WebGLRenderer**

Рендер на технологии WebGL. В примере ниже рендереру задают размеры как DOM-элементу и добавляют на страницу в body. По поводу рекурсии посмотри еще как это в уроке 2 было [сделано](#lesson-3-renderer-recursion-update-function).

```javascript
let renderer = new THREE.WebGLRenderer();

// задаем размер рендерера (канваса)
renderer.setSize(window.innerWidth, window.innerHeight);
// и добавляем его на страницу
document.body.appendChild(renderer.domElement);
```

```javascript
// вариант реализации рекурсивной функции рендера приложения

function update() {
  // здесь описывается что должно происходить каждый кадр:
  // анимация, перемещение объектов и т.д. 
  renderer.render(сцена, камера)
  requestAnimationFrame( function () { 
    update();
  });
};
```







<!-- Ссылки -->
[toc]: #содержание
[webvkube]: http://webvkube.ru
[youtube_main_channel]: https://www.youtube.com/channel/UCBnK0ae8Wvu_TEkWmOIwWBw
[vk_kurspothreejs]: https://vk.com/kurspothreejs
[vscode_intellisense]: http://shrekshao.github.io/2016/06/20/vscode-01/
[three_js_site]: http://threejs.org
[three_js_github_build]: https://github.com/mrdoob/three.js/tree/dev/build
[three_js_doc_site]: https://threejs.org/docs/index.html#manual/en/introduction/Creating-a-scene