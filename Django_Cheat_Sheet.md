### Básico
django-admin stratproject name .

python managy.py runserver

python manage.py startapp appname

------------------------------

python manage.py makemigrations users

python manage.py sqlmigrate appName 0001

python manage.py check

python manage.py migrate

------------------------------

python manage.py createsuperuser

python manage.py test

------------------------------
### API database
python manage.py shell

	from polls.models import Choice, Question

	Question.objects.all()

	Question.objects.filter(id=1)

	Question.objects.filter(question_text__startswith='What')

### Get the question that was published this year.
	>>> from django.utils import timezone
	>>> current_year = timezone.now().year
	>>> Question.objects.get(pub_date__year=current_year)
	<Question: What's up?>

### Exemplos:
	Question.objects.get(id=2)
	Question.objects.get(pk=1)

	q = Question.objects.get(pk=1)
	q.was_published_recently()

-------------------------------

django-admin makemessages --all

django-admin compilemessages

-------------------------------

python manage.py dumpdata courses --indent=2

python manage.py dumpdata --help

python manage.py dumpdata courses --indent=2 --output=courses/fixtures/subjects.json

python manage.py loaddata subjects.json
