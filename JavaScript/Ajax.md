# Ajax (Asynchronous Javascript And XML)

> 비동기적인 웹 제작을 위해 기술들의 조합을 이용하는 웹개발 기법.

techs

```
  - HTML & CSS
  - DOM & JavaScript
  - XML & XSLT ( XML 문서를 다른 XML 문서로 변환하는데 사용하는 XML 기반 언어 /
원본 XML 기반으로 새로운 XML 생성 ) & XHR => 웹 서버와 비동기적으로 데이터를 교환하고 조작함
```

- cdn

  - vue js cdn 검색 - 복사 후 기입

- scrollmonitor

  ```jsx
  <script src="<https://cdnjs.cloudflare.com/ajax/libs/scrollmonitor/1.2.0/scrollMonitor.js>" ></script>
  ```

- Axios

  > Promise 기반 HTTP 통신 라이브러리. 문서화가 잘되어 있고 API가 다양함.

  ```jsx
  <script src="<https://cdn.jsdelivr.net/npm/axios/dist/axios.min.js>"></script>
  ```

  ```jsx
  <div id="app">
    <button v-on:click="fetchData">get data</button>
  </div>
  ```

  ```jsx
  new Vue({
    el: '#app',
    methods: {
      fetchData: function() {
        axios.get('<https://jsonplaceholder.typicode.com/users/>')
          .then(function(response) {
            console.log(response);
          })
          .catch(function(error) {
            console.log(error);
          });
      }
    }
  })
  ```

  axios.get에서 then의 콜백함수의 인자는 get해서 얻어온 것이 들어간다.

- Promise => 성공/실패

  > 당장 할 수 있는 것과 "아닌 것"

  - 불확실하고 기다려야하는 작업(AJAX, axios)을 비동기적으로 처리하기 위해서 + 그러한 작업만을 위함
  - method: 외부요청(XHR), 기다리는 것(settimeout)

- ex of 비동기적 처리

  ```jsx
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>Document</title>
  </head>
  <body>
      <script>
          const xhr = new XMLHttpRequest()
          xhr.open('GET', 'https: koreanjs~~~')
          xhr.send() //아직 끝나지 않
  
          const res = xhr.response
          console.log('RES:', res)
  
      </script>
  </body>
  </html>
  ```

  ```jsx
  > xhr.response
  < "{"id":1, "title": "정당의 목적이나 ~~~"}"
  
  > res === ""
  < true
  ```

  : 파이썬은 인터프리터언어로 블럭킹하면서 넘어가고, JS도 그렇지만, DOM에서 제공하는 몇몇 매서드가 코드 하나하나 안 기다려주고 넘어감.

- caution

  - 콜백 함수를 쓴다 => non-blocking한 비동기 작업한다 (X)
  - non - blocking 한 비동기 작업을 한다. => 콜백을 쓸 수 밖에 없도록 설계되어 있다

- XML (Extensible Markup Language)

  - 구조적인 데이터를 위한 것이다.
  - 다소 [HTML](https://ko.wikipedia.org/wiki/HTML) 같이 보인다.
  - 텍스트이며, 읽히는 것만을 뜻하지 않는다.
  - 크기가 커진다.
  - 기술의 [집합](https://ko.wikipedia.org/wiki/집합)이다.
  - 새로운 기술이 아니라 발전한 기술이다.
  - [HTML](https://ko.wikipedia.org/wiki/HTML)에서 [XHTML](https://ko.wikipedia.org/wiki/XHTML)로 이끌었다.
  - 모듈식이다.
  - [RDF](https://ko.wikipedia.org/wiki/RDF)와 [시맨틱 웹](https://ko.wikipedia.org/wiki/시맨틱_웹)의 토대이다.
  - [라이선스](https://ko.wikipedia.org/wiki/라이선스) 제약이 없으며, [플랫폼](https://ko.wikipedia.org/wiki/플랫폼)이 독립적이고, 많은 지원이 있다.

- XHR (XMLHttp request)

  > 브라우저와 서버 간 "메소드가 데이터를 전송"하는 "객체 형태의" API

  > Ajax 를 보낼 수 있는건 XHR밖에 없는데, 예를 쉽게 쓸 수 있도록 해주는 axios

  - ex) 자동완성

> MVVM 패턴

> ex) 페북이나 구글맵에서 한 페이지 안에서 요청이 일어남.

> JS는 작업환경인 Document(tab)이 싱글스레드이기 때문에, 비동기(어떤 작업을이 종료될 때까지 기다리지 않고, 다른 작업을 하고 있다가, 요청한 작업이 종료되면, 그에 대한 추가 작업을 이어서 수행) 요청을 보낸다.