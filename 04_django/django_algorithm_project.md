# Algorithm project



dummy data 넣기

- Faker 
- django-extensions
  - python manage.py shell_plus
  - shell_plus 에서 python code 실행



query문 실험하기

- database access optimization
- https://docs.djangoproject.com/en/3.2/topics/db/optimization/
- Understanding QuerySet evaluation
  -  querysets are lazy
  - when they are evaluated
  - how the data is held in memory
- debug toolbar
  - https://django-debug-toolbar.readthedocs.io/en/latest/installation.html
  - 중복되는 쿼리를 줄이기
  - 1+N query problem



## annotate

review table에 컬럼 추가하기

- views.py



- comment count

```python
from django.db.models import Count
reviews = Review.objects.annotate(Count('comment')).order_by('-pk')  # comment model 의미
```



```django
{{ review.comment__count }}
```





## join

- user username

```python
reviews = Review.objects.select_related('user').order_by('-pk') # 정참조 innerjoin 
```



### select_related

- FK 정참조
  - review(N)에 user(1) 정보를 가지고 있는데 (ForeignKey) = 정참조
  - (user가 review 참조하면 역참조) 
- sql 이 join



### prefetch_related

- Many To Many 정참조
- FK 역참조
- python 내부에서 join



- review 가 가진 comment
  - 역참조

```django
{% for comment in review.comment_set.all %}
	{{ comment }}
{% end for %}
```



```python
reviews = Review.objects.prefetch_related('comment_set').order_by('-pk')
```





### 종합

```python
from django.db.models import Prefetch

reviews = Review.objects.prefetch_related(
Prefetch('comment_set',    queryset = Comment.objects.select_related('user')))
.order_by('-pk')
```

