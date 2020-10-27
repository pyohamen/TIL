# ES \(ECMAscript\)

* **Caution**

  let: 재 할당 가능 / const: 재할당 불가능 !== 값이 바뀌지 않음.

  Function =&gt; 1급 객체

  변수\(var\)나 데이터 구조안에 담을 수 있다

  파라미터로 전달 할 수 있다 \(함수의 인자\)

  리턴 값으로 사용할 수 있다

  절대 느슨한 일치 연산자 \(==, !=\)를 사용하지 않는다 \| ===, !==

  Can't ~~ js는 문장띄운것을 합쳐 보기 때문에 ; 가 없어서 에러 날 수 있다

* **`console.log()` : 콘솔창에 메시지를 출력**
* 요소\(querySelctor'잡은' / createElement'만든'\)를 잘 만들어서\(innerText or innerHTML\) 붙인다.\(Node.append\(\) or appendchild\(\)\)
* **callback function**
  * array helper method -&gt; callback function \(for 이벤트리스터 of DOM / 1급객체\)

    > A callback function is a function passed into another function as an argument, which is then invoked inside the outer function to complete some kind of routine or action.

  * map\(\): 각 value가 인자 자리에 들어가 리턴된 값을 새로운 배열에 넣어 리턴함
  * forEach\(\): 인자에 value들을 받아 넘겨주고 끝, 리턴없음
  * Filter\(\): 리턴이 true인 value들만 모아 새로운 배열로 리턴
* **This**

  > this 가 window가 아닌 경우,method 안의 this -&gt; 해당 method가 정의된 객체\(object\)생성자 함수 안의 this

