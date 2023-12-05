# Coroutine이란?

### 코루틴(Coroutine이란, Co + Routine의 의미로써 상호협력하는 루틴이라고 볼 수 있다. 혹은 상호 연계 프로그램, 또는 함수를 일컫는다.

그렇다면 상호협력하는 루틴이라는 건 무엇인지 헷갈리게 됩니다.
두 함수를 비교해서 한번 직관적으로 알아보겠습니다.

먼저, 두 개의 수를 더하는 함수를 호출하는 메인 함수를 코드로 작성 해보겠습니다.
```python
def add(a, b):
  c = a + b
  print(c)
  print("add 함수")

def calc():
  add(1, 2)
  print("calc 함수")

calc()
```

위의 코드를 보면 **calc**함수 안에서 **add**함수를 호출하고 **add**함수가 끝나면 다시 **calc**로 돌아옵니다.
**add**함수가 끝남과 동시에 **add**함수에 들어있던 변수와 계산식은 종료되고 모두 사라지게 됩니다.]

이를 우리는 보통 **메인 루틴에서 서브 루틴을 호출하고 서브 루틴을 종료된다** 라고 얘기 할 수 있습니다.

하지만, 코루틴은 방식이 다르다고 할 수 있습니다.
위의 메인 루틴과 서브 루틴이 종속적인 관계가 아니라, 서로 대등한 관계이며 특정 시점에 상대 코드를 실행합니다.

아래가 코루틴 예시 코드 중 하나입니다.
```python
def sum_coroutine():
    total = 0
    while True:
        x = (yield total)
        total += x

def sum_func():
    co = sum_coroutine()
    next(co)
    result1 = co.send(10)
    print(f"result1 --> {result1}")
    result2 = co.send(20)
    print(f"result2 --> {result2}")

sum_func()
```

**sum_func**과 **sum_coroutine**의 객체 **co**가 서로 값을 주입하고 결과를 전달받아 상호 협력적으로 작동하는 것을 확인 할 수 있습니다.

중요한 것은 **sum_coroutine**이 한번 실행 후 종료되는 것이 아니라, 계속 **co**에게 **send**함수를 통해 값을 전달하고 대기하고 있는 것을 알 수 있습니다.

그림으로 표현하면 아래와 같습니다.

<p align="center"><img src="https://velog.velcdn.com/images/jaebig/post/7cdbfe9c-8449-4537-92c5-8a8dcecc123a/image.jpeg" width="450px" height="500px" title="" alt="RubberDuck"></img></p><br/>

위와 같은 성질 때문에 코루틴을 **협력형 멀티 테스킹을 위한 함수 또는 프로그램**이라고 합니다.

추가적으로 **sum_coroutine**이 한번 실행하고 종료되는 것이 아니라, "대기" 하고 있다고 말씀드렸는데요,
이는 즉 코루틴은 비동기 처리가 가능하도록 하며, 코루틴 함수들을 잘 조합하여 사용하면, **동시성(Concurrency) 프로그래밍**   또한 가능합니다

이처럼 코루틴은 기본적으로 특정 지점에서 실행을 일시 중지할 수 있는 함수이며, 나중에 원할 때마다 같은 지점에서 실행을 재개할 수 있습니다.
