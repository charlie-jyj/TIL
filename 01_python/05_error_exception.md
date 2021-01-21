# 에러& 예외 처리



## 문법 오류

1. 제어문, 함수 :
2.  string quotation 



## 예외(exception)

1. ZeroDivisionError
2. NameError : 스코프를 뒤져봐도 defined된 변수가 없다.
3. TypeError: 해당 타입이 지원하지 않는 연산이나 메소드, argument 부족/초과
4. ValueError: invalid literal, value is not in list
5. IndexError: 존재하지 않는 index 조회
6. KeyError: dict에서 존재하는 key가 없을 경우
7. ModuleNotFoundError : 모듈을 찾을 수 없는 경우
8. importError: 모듈을 찾았지만 임포트 실패
9. KeyboardInterrupt:  강제 종료되었을 때



## 예외 처리

> try-catch



- try-catch
- raise : 예외 강제 발생 (사용자 정의 에러 클래스의 메시지를 보여줄 수 있다.)
- assert :  AssertionError 발생, 상태를 검증하는데에 사용된다. test 후에 문제가 생기는 코드에 대해 assert
- 원래 error 발생시 코드가 멈추지만 예외처리를 할 경우 코드가 끝까지 동작한다.
- `as` 키워드 사용하여 에러메시지를 보여줄 수 있다.
- 복수의 예외 처리 가능 (tuple로 저장)
- 복수의 에러는 순차적으로 수행된다.  (작은 범주부터 시작)



```python
def dealWithException:
	try:
		'에러가 발생할 수 있는 코드 블럭'
	except (예외1, 예외2) as err:
		f'{err} 발생시 수행되는 코드'
    except 예외3 as err:
		f'{err} 발생시 수행되는 코드'
    else:
        '에러가 발생하지 않는 경우 수행되는 코드'
    finally:
        '예외 발생 관련없이 무조건 동작하는 코드'
        
	func()  # 오류가 발생해도 예외처리 했기 때문에 func는 call된다.
```



