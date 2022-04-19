# yamdb_final
yamdb_final
http://62.84.121.191/admin/
![example workflow](https://github.com/DipperPain/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)
Проект YaMDb собирает отзывы (Review) пользователей на произведения (Title). Произведения делятся на категории: «Книги», «Фильмы», «Музыка». Список категорий (Category) может быть расширен (например, можно добавить категорию «Изобразительное искусство» или «Ювелирка»).
###
Сами произведения в YaMDb не хранятся, здесь нельзя посмотреть фильм или послушать музыку.

В каждой категории есть произведения: книги, фильмы или музыка. Например, в категории «Книги» могут быть произведения «Винни Пух и все-все-все» и «Марсианские хроники», а в категории «Музыка» — песня «Давеча» группы «Насекомые» и вторая сюита Баха. Произведению может быть присвоен жанр из списка предустановленных (например, «Сказка», «Рок» или «Артхаус»). Новые жанры может создавать только администратор.

Благодарные или возмущённые читатели оставляют к произведениям текстовые отзывы (Review) и выставляют произведению рейтинг (оценку в диапазоне от одного до десяти). Из множества оценок автоматически высчитывается средняя оценка произведения.
Подготовка к работе:
###
Клонируем репозиторий на локальную машину и перейдите в рабочую директорию:

git clone https://github.com/dipperpain/yamdb_final.git

В корневой папке находим файл .env.template. По образу и подобию необходимо создать файл .env и заполнить его своими значениями.
###
Запускаем процесс сборки и запуска контейнеров:

docker-compose up
###
Запускаем терминал внутри контейнера (на вин системах используйте winpty docker-compose exec web bash ):

docker-compose exec web bash
###
Накатываем миграции:

python manage.py migrate
###
Собираем статику:

yamdb_web_1 python manage.py collectstatic --no-input
###
Создаем суперюзера:

yamdb_web_1 python manage.py createsuperuser
###
Загружаем в базу тестовые данные:

yamdb_web_1 python manage.py loaddata fixtures.json
###
Остановить работу и удалить контейнеры можно командой:

docker-compose down
