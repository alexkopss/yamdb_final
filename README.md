# Educational project: [yamdb_final](http://62.84.122.16/admin)
RestAPI for Custom Imdb service - database of movies, books, music reviews
## About
API for the Custom IMDB service. Allows you to work with:

- **_Reviews_** Get a list of all reviews, create a new review, get a review by id, partially update a review by id, delete a review by id

- **_Review comments_** Get list of all review comments by id, create new review comment, get review comment by id, partially update review comment by id, delete review comment by id

- **_JWT token_** Sending confirmation_code to the given email, receiving JWT token in exchange for email and confirmation_code

- **_Users_** Get a list of all users, create a user, get a user by username, change user details by username, delete a user by username, get their account details, change their account details

- **_Categories (types) of works_** Get a list of all categories, create a category, delete a category

- **_Genre categories_** Get a list of all genres, create a genre, delete a genre

- **_Reviewed artworks_** Get a list of all items, create a review item, item info, update item info, delete item


## [Documentation(ru)](http://62.84.122.16/redoc/)

## .env-file template:


```
DB_ENGINE=django.db.backends.postgresql
DB_NAME=postgres
POSTGRES_USER=postgres
POSTGRES_PASSWORD=postgres
DB_HOST=db
DB_PORT=5432
```

## How to start:
- Install docker and docker-compose:
Use official documentation [here](https://docs.docker.com/engine/install/)
- Clone the repository and change directory into it on the command line:
```
git@github.com:Alastor047/yamdb_final.git
```
- Run migrations:

```
docker-compose exec web python manage.py migrate
```
- Create superuser:
```
docker-compose exec web python manage.py createsuperuser
```
- Collect static:
```
docker-compose exec web python manage.py collectstatic --no-input
```
- Check if the app is working, login to django admin [here](http://62.84.122.16/admin/)
- Upload dump **fixtures.json**:
```
python3 manage.py shell
```
```
from django.contrib.contenttypes.models import ContentType
```
```
ContentType.objects.all().delete()
```
```
quit()
```
```
python manage.py loaddata dump.json
```
## Endpoints for example
- Create User        http://62.84.122.16/api/v1/auth/signup/
```
{ "email": "string", "username": "string" }
```
- Get Jwt Token      http://62.84.122.16/api/v1/auth/token/
```
{ "username": "string", "confirmation_code": "string" }
```
- Category List      http://62.84.122.16/api/v1/categories/
- Genre List         http://62.84.122.16/api/v1/genres/
- Title List         http://62.84.122.16/api/v1/titles/
- Review List        http://62.84.122.16/api/v1/titles/1/reviews/
- Comment List       http://62.84.122.16/api/v1/titles/1/reviews/1/comments/
- User List          http://62.84.122.16/api/v1/users/
- User self profile  http://62.84.122.16/api/v1/users/me/
- _You can also add the id number to the end of the **List-endpoint** path to get a separate instance as shown here:_
http://62.84.122.16/api/v1/titles/1/reviews/1
###### You will see this response:
![Response](https://user-images.githubusercontent.com/99352898/175463539-8f316740-144f-40b6-943e-66305e04d46c.jpg)

## Author:
[Andrey Kruglov](https://github.com/Alastor047)





![](https://img.shields.io/pypi/pyversions/p5?logo=python&logoColor=yellow&style=for-the-badge)
![](https://img.shields.io/badge/Django-2.2.16-blue)
![](https://img.shields.io/badge/DRF-3.12.4-lightblue)
![Docker Automated build](https://img.shields.io/docker/automated/alastor047/api_yamdb?color=1&label=v1.0)
[![Django-app workflow](https://github.com/Alastor047/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)](https://github.com/Alastor047/yamdb_final/actions/workflows/yamdb_workflow.yml)