# Document Object Model

> html이 메모장에서는 그냥 string이지만, browser에서는 해석해서 `구조화`\(DOMtree\) 를 해서 DOM이 된다.

Console에서 type of document 할 시, 결과로 object가 return 되는 것을 볼 수 있다.

DOM 조작: parsing된 html, 즉 DOM{~~~} DOM안의 내용을 조작하는 것을 의미함

It means 문자열탐색 -&gt; Tree 탐색 \(Tree의 하나하나는 Node가 된다\) / 서버없이 정적인 상태에서도 Programmable한 문서가 될 수 있다. / MTV 과정 생략하고 browser를 코딩할 수 있음

1. 선택
   1. document.querySelector\(\)

      Node를 찾자! / Element에서 copy -&gt; selector 로 ''으로 묶어 인자를 넣어주자: 주어를 잡음

      * .innerHTML
      * .classlist: parsing해줌 / .classlist.add: 동적으로 class를 추가할 수 있음
2. 수정
   * document.querySelector\(셀렉터\).innerText = "!!!"
3. 생성
   * point: 문서에서 대상을 잡고, 수정하고, 생성하는데 str하드타이핑 방식이 아닌, **객체** 를 잡아서 조작하자
4. 이벤트리스터

   요소.addEventListener\('이벤트', 이벤트 발생시 실행할 함수\)

   ```jsx
   myButton.addEventListener('click', confirmMessage)
   ```

   addEventListener의 인자인 실행함수는, 등록해놓은 함수를 실행하는 느낌으로 가야함, 실행함수의 인자는 이벤트객체임

