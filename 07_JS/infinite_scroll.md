

- fixture

```python
python manage.py loaddata movies.json
```



https://docs.djangoproject.com/en/3.2/topics/pagination/



```python
from django.core.paginator import Paginator
from django.shortcuts import render

from myapp.models import Contact

def listing(request):
    contact_list = Contact.objects.all()
    paginator = Paginator(contact_list, 25) # Show 25 contacts per page.

    page_number = request.GET.get('page')
    page_obj = paginator.get_page(page_number)
    return render(request, 'list.html', {'page_obj': page_obj})
```



## axios 로 요청 보내기



```javascript
document.addEventListener('scroll', (event)=>{})
```





### scrollTop

- 현재 내 스크롤 위치에서 상단 끝까지 남아있는 높이



### clientHeight

- 내가 지금 보고있는 화면 영역의 높이



### scrollHeight

- 전체 문서의 높이
  - 스크롤 했을 때 내가 볼 수 있는 처음과 끝



### 요소를 끝까지 스크롤 했는지 판별하기

```javascript
element.scrollHeight - Math.abs(element.scrollTop) === element.clientHeight
```

https://developer.mozilla.org/ko/docs/Web/API/Element/scrollHeight





### json 데이터 받기



- 1~10  html
  - 첫화면은 html로 보내주어야
- 11~10 json
  - AJAX 요청
- 21~30 json
  - AJAX 요청



```python
 # 분기처리 (첫 페이지 요청/ AJAX 요청)
    if request.is_ajax():
        data = serializers.serialize('json', articles)
        return HttpResponse(data, content_type='application/json')
        
    else:
        context = {
            'articles': articles,
        }
        return render(request, 'articles/index.html', context)
```

- 한편, axios 로 요청을 보낸다고 해서 AJAX 요청으로 django 가 이해하는 것은 아니기 때문에
- headers 수정이 필요하다



```javascript
  // axios 로 보낸다고 AJAX 요청으로 django가 판단하는 것은 아님
        axios({
          method: 'get',
          url: URL,
          headers: {'X-Requested-With': 'XMLHttpRequest'},
        })
          .then((res)=>{
            console.log(res)
          })
```

