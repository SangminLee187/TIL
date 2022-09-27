# RxJS
```
회사코드를 분석하다보면 Observable과 subscribe메소드를 볼 수 있었다.
```

### 개념
* Reactive Extensions for JavaScript
* **반응형 프로그래밍** 은 비동기 프로그래밍 패러다임중 하나
* **옵저버블** 을 사용하는 JavaScript 라이브러리
* 비동기 코드를 직관적이고 가독성 좋게 작성할 수 있다.
* 생산자/소비자/관찰자의 개념

### 반응형 프로그래밍
* **데이터 스트림** 과 **변화전파** 와 연관된 선언적 프로그래밍 패러다임
  - 데이터 스트림 : 계속 관찰할 수 있는 연속적인 흐름을 가진 데이터
  - 변화전파 : 상태가 계속 변하는 객체와 그 상태를 계속 관찰하고 변화를 전달하는 객체로 이루어진 패턴
![image](https://user-images.githubusercontent.com/97998574/192435954-0170d4fd-3d64-41f1-85dc-624ad87a8b32.png)


### 주요개념
#### Observable
* 시간의 흐름에 따라 도착하는 스트림 또는 데이터의 출처
```TypeScript
// fromEvent 연산자를 가져옵니다
import { fromEvent } from 'rxjs';

// button을 참조
const button = document.getElementById('myButton');

// 버튼 클릭 옵저버블을 생성합니다
const myObservable = fromEvent(button, 'click');
```
* LifeCycle : 생성-.create(); // 구독-.subscribe(); // 실행-.next(); // 구독해제-.unsubscribe();

#### Subscription
* 옵저버블을 동작
* subscription을 만들기 위해서는 observer라고 부르는 함수와 함께 subscribe 메소드를 호출
```
// fromEvent 연산자를 가져옵니다
import { fromEvent } from 'rxjs';

// button을 참조
const button = document.getElementById('myButton');

// 버튼 클릭 옵저버블을 생성합니다
const myObservable = fromEvent(button, 'click');

// 자, 이젠 클릭할 때 마다 로그를 생성합니다
const subscription = myObservable.subscribe(event => console.log(event));
```

``` myObservable.subscribe() ``` 역할
* 버튼에 클릭 이벤트에 대한 이벤트 리스너 설정
* 매 클릭 이벤트마다 subscribe메소드와 함께 넘겨준 함수(observer)를 실행
* 적절한 이벤트 리스너 삭제와 같은 일을 하는 unsubscribe와 함께 Subscription 객체를 반환
