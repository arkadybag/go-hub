Хаб для кластера из браузеров.<br>
Отлично подходит для __auto scaling__ систем, таких как __AWS EC2__.

Хаб запоминает все узлы, которые регистрируются у него. Он создается с в контейнере __docker__ c переменной окружения __token__. Эта переменная, в последствии, служит для проверки его с токеном узла, который хочет зарегистрироваться.

Регистрация узла в хабе происходит автоматически при его создании. Контейнер узла создается со следующими переменными окружения: __token__ и __server__. Токен должен быть такой же как и у хаба, в переменную сервер указывается адрес хаба.

Команда для запуска хаба: <br>
1.  ```go build .```<br>
2.  ```docker build ./ -t hub```<br>
3.  ```docker run -ti --rm -p 8080:8080 -e "token=TOKEN" hub```<br>

Узел - это docker контейнер, который имеет один открытый порт, внутри себя скрывает отдельно запущенный phantomjs - https://github.com/arkadybag/go-phantomjs-node
