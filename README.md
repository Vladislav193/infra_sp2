Проект YaMDb собирает отзывы пользователей на произведения. Сами произведения в YaMDb не хранятся, здесь нельзя посмотреть фильм или послушать музыку. Произведения могут быть разных типов:

музыка🎼
фильмы🎬
книги📚
Так же есть возможность добавить новые категории. Произведения делятся на жанры. Администратор может добавлять произведения, категории и жанры. Пользователи могут оставлять отзывы, оценку произведения от 1 до 10. из оценок у произведения сформируется рейтинг. Другие пользователи смогут оставлять комментарии к отзывам. Добавлять отзывы, комментарии и ставить оценки могут только аутентифицированные пользователи.

### Шаблон создания файла .env с переменными окружения для работы с базой данных:
# указываем, что работаем с postgresql
DB_ENGINE=django.db.backends.postgresql 
# задаем имя базы данных
DB_NAME=postgres
# логин для подключения к базе данных
POSTGRES_USER=login
# пароль для подключения к БД (установите свой)
POSTGRES_PASSWORD=pass
# название сервиса (контейнера)
DB_HOST=db
# порт для подключения к БД
DB_PORT=5432

### Команды для запуска приложения в контейнерах:

# Скопируйте репозиторий.
git clone <ссылка HTTPS/SSH>
# Перейдите в папку infra:
cd  infra/
# Создайте файл с переменными окружения .env(Шаблон наполнения выше)
# Запускаем docker-compose:
docker-compose up
# В контейнере web выполните миграции:
docker-compose exec web python manage.py migrate
# Создатйте суперпользователя:
docker-compose exec web python manage.py createsuperuser
Для пользователей windows 11:
winpty docker-compose exec web python manage.py createsuperuser
# Соберите статику:
docker-compose exec web python manage.py collectstatic --no-input

### Заполнение базы данныхЖ
Перейдите по ссылке http://localhost/admin/ , авторизуйтесь и заполните базу данных

# Можно создать резервную компию:
docker-compose exec web python manage.py dumpdata > fixtures.json 


