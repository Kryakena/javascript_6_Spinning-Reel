# Крутящийся барабан

Источник: 
видео "Уроки по JavaScript. Делаем игру крутящийся барабан на Джаваскрипт" 
https://vkvideo.ru/video-101965347_456257148?sel=19460369

Барабан крутится в случайном направлении и останавливается в рандомном положении.

# Алгоритм работы:

1. Создать нужные файлы

- создаем HTML (index.html), CSS (style.css), JS (script.js) документ в программе "WebStorm" для работы с JavaScript 
(скачать бесплатную версию https://www.jetbrains.com/webstorm/);

2. в файле index.html:

- меняем название в строке title в разделе head - Барабан

  ```html
  <title>Барабан></title>
  ```

- Указываем указатель для крутящегося барабана. А чтобы вид стрелки был симпатичный, 
берем с сайта с символами юникод (пример: https://symbl.cc/ru) 
символы стрелок и вставляем в кнопки в файле index.html в разделе body

  ```html
  <p>🢛</p>
  ```

- указатель для барабана заключаем в div, чтобы отделить её от нашего барабана. Называем класс div arrow (стрелка)

  ```html
  <div class="arrow">
    <p>🢛</p>
  </div>
  ```
  
- создаем заранее div с классом circle

  ```html
  <div class="circle"></div>
  ```

3. в файле style.css указать url (https://polechudes.tv/images/baraban.png) на изображение 

  ```css
  .circle{
    background-image: url("https://polechudes.tv/images/baraban.png");
  }
  ```

4. в файле index.html подцепляем стиль из CSS файла в разделе head

  ```html
  <link rel="stylesheet" href="style.css">
  ```

5. в файле style.css описываем изображение в .circle

  ```css
  height: 700px;
  width: 700px;
  border-radius: 9999px; /*максимально скругляем углы*/
  border-color: aqua;
  ```

6. в файле style.css ставим изображение в центр и закрепляем размер в .circle

  ```css
  background-position: center;
  background-size: cover;
  ```

7. в файле style.css описываем стиль для стрелочки в отдельном теге p

  ```css
  p{
    position: relative;
    left: 330px; /*чем выше пиксели, тем правее стрелочка. Надо установить её по центру над изображением*/
    font-size: 70px;
  }
  ```

8. чтобы барабан крутился - в файле script.js

  ```JS
  document.getElementsByClassName('circle')[0].addEventListener('click', function(e){
    e.target.style.transform = 'rotate('+Math.random()*1000+'rad)';
  });
  ```

9. в файле index.html подцепляем скрипт из JS файла в разделе body после указанного класса барабана

  ```html
  <script src="script.js"></script>
  ```

10. в файле script.js - чтобы барабан постоянно двигался, а не при нажатии, 
указываем в getElementsByClassName - return false

  ```JS
  return false;
  ```

11. в файле style.css в .circle дополняем описание барабана - 
чтобы он сам крутился или перезапускался при нажатии и выдавал значение через 5 секунд, если нет нажатий

  ```css
  transition: 5s; /*колесо будет двигаться 5 секунд*/
  transition-timing-function: ease-in-out; /*через сколько времени можно его двигать*/
  ```