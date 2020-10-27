# 01\_Vue.js\_Intro

## 01\_Vue.js\_Intro

## Start

```jsx
<script src="<https://cdn.jsdelivr.net/npm/vue/dist/vue.js>"></script>
```

## Intro

* el \( Vue 의 인스턴스로 어느 요소에 마운트할지 결정 \)

  ```jsx
  <body>
      <div id='app' >  <!-- 하나의 부모요소를 갖음 -->

      </div>

      <script src="<https://cdn.jsdelivr.net/npm/vue/dist/vue.js>"></script>

      <script>
          // el 은 Vue 인스턴스의 속성으로 어떤 요소에 마운트할지 결정
           const app = new Vue ({
              el: '#app', 
           })
           console.log(app) => Vue
           console.log(app.$el) => <div id="app"></div>
      </script>

  </body>
  ```

* data \( 호출 시, app.data.message \( X \), app.message \( O \) \)

  ```jsx
  <body>
      <div id="app">
      </div>

      <script src="<https://cdn.jsdelivr.net/npm/vue/dist/vue.js>"></script>
      <script>
          const app = new Vue({
              el: '#app', //어떤 요소에 마운트할지
              data: {    // MVVM => Model 이다. data 가 핵심!
                  message: 'Hello Vue'
              },
          })
          console.log(app.message) => Hello Vue

      </script>
  </body>
  ```

* interpolation \(  \) 보간법

  ```jsx
  <body>
      <div id="app">
          {{ message }} 
      </div>

      <script src="<https://cdn.jsdelivr.net/npm/vue/dist/vue.js>"></script>
      <script>
          const app = new Vue ({
              el: '#app',
              data: {
                  message : 'Hello Vue',
              }
          })

      </script> 

  </body>
  ```

* v-text / if / if-elseif-else / for / bind \( v- 접두사로 시작하는 디렉티브 \( 명령하는 것 \) \)

  ```jsx
  <body>

      <div id="app">
          text, if, if-elseif-else, for 까지는 쉬우니 패스
                  <a href="{{ googleUrl }}">Bad Google link</a>
          <!-- v-bind: 표준 HTML 속성과 Vue 인스턴스를 연동할 때. (+a) -->
          <a v-bind:href="googleUrl">Good Google link</a>
          <a href="{{ naverUrl }}">Bad Naver link</a>
          <a v-bind:href="naverUrl">Good Naver link</a>
          <img v-bind:src="randomImageUrl" v-bind:alt="altText">
      </div>

      <script src="<https://cdn.jsdelivr.net/npm/vue/dist/vue.js>"></script>
      <script>
          const app = new Vue ({
              el: '#app',
              data: {
                                  googleUrl: '<https://google.com>',
                  naverUrl: '<https://naver.com>',
                  randomImageUrl: '<https://picsum.photos/200>',
              }})
      </script>
  </body>
  ```

`v-bind:` : `:` 으로 쓸 수 있다.

* method / v-on

  ```jsx
  <div id="app">
          {{ message }}
      </div>
      <script src="<https://cdn.jsdelivr.net/npm/vue/dist/vue.js>"></script>
      <script>
          const app = new Vue({
              el: '#app',
              data: { // 인스턴스
                  message: 'Hello Vue'
              },
              methods: { // 함수들의 집합, data를 가지고 움직일 수 있게 됨
                  alertWarning: function () {
                      alert('WARNING')
                  },
                  alertMessage () { // Syntactic Sugar: 위와 아래 완전히 같음
                      alert(this.message)
                  },
                  changeMessage () {
                      this.message = 'CHANGED MESSAGE'
                  },
              }
          })
      </script>
  </body>
  ```

  \`\`\`jsx

     {{ message }}

  ```text
      <button v-on:click="alertWarning">Alert Warning</button>
      <button v-on:click="alertMessage">Alert Message</button>
      <button v-on:click="changeMessage">Change Message</button>
      <hr>
      <input @keyup.enter="onInputChange" type="text" name="" id="">
  </div>

  <script src="<https://cdn.jsdelivr.net/npm/vue/dist/vue.js>"></script>
  <script>
      const app = new Vue({
          el: '#app',
          data: {
              message: 'Hello Vue'
          },
          methods: {
              alertWarning: function () {
                  alert('WARNING')
              },
              alertMessage () {
                  alert(this.message)
              },
              changeMessage() {
                  this.message = 'CHANGED MESSAGE'
              },
              onInputChange(event) {
                  // if (event.key == "Enter") {
                      this.message = event.target.value
                  },

          }
      })

  </script>
  ```

&lt;/body&gt;

```text
`v-on:`  : `@` 으로 쓸 수 있다.

- v-model

  ```jsx
  <body>
      <div id="app">
          <h1>{{ message }}</h1>
          <!-- 사용자 입력 <=> data 를 완전히 동기화 시키고 싶다 -->
          <!-- v-model => input, select, textarea 에 양방향 바인딩 -->

          <hr>
          <!-- 단방향 바인딩 (input => data) -->
          1way:
          <input v-on:keyup="onInputChange" type="text">
          <hr>
          <!-- 양방향 바인딩 (input <=> data) -->
          2way:
          <input v-on:keyup="onInputChange" type="text" :value="message">
  value 가 표준속성이기 때문에 v-bind 해줘야함
          <hr>
          <!-- v-model -->
          v-model/2way:
          <input v-model="message" type="text">
      </div>
      <script src="<https://cdn.jsdelivr.net/npm/vue/dist/vue.js>"></script>

      <script>
          const app = new Vue({
              el: "#app",
              data: {
                  message: 'hi',
              },
              methods: {
                  onInputChange(event) {
                      this.message = event.target.value
                  }
              }
          })
      </script>

  </body>
```

* v-show

  ```jsx
  <body>
      <div id="app">
          <button @click="changeF" >changeF</button>
          <!-- v-if 는 평가(t/f)가 자주 바뀌지 않을때 유리하다 => 초기 코스트가 적다. -->
          <p v-if="t">
              This is v-if
          </p>

          <p v-if="f">
              This is v-if with false
          </p>

          <!-- v-show 는 평가(t/f) 가 자주 바뀔 때 유리하다 => 토글 코스트가 적다 -->
          <p v-show="t">
              This is v-show with true
          </p>

          <p v-show="f">
              This is v-show with false
          </p>

      </div>
      <script src="<https://cdn.jsdelivr.net/npm/vue/dist/vue.js>"></script>
      <script>
          const app = new Vue({
              el: "#app",
              data: {
                  t: true,
                  f: false,
              },
              methods: {
                  changeF () {
                      this.f = !this.f
                  }
              }
          })
      </script>

  </body>
  ```

* lodash

  ```jsx
  <body>
      <div id="app">
          <button @click="getLuckySix">GET LUCKY 6</button>
          <ul >
              <li v-for="number in myNumbers">
                  {{ number }}
              </li>
          </ul>
      </div>
      <script src="<https://cdn.jsdelivr.net/npm/vue/dist/vue.js>"></script>
      <script src="<https://cdnjs.cloudflare.com/ajax/libs/lodash.js/4.17.20/lodash.min.js>"></script>
      <script>
          const app = new Vue({
              el: "#app",
              // [1..45] 에서 6개를 랜덤하게 뽑는다.
              data: {
                  allNumbers: _.range(1,46),
                  myNumbers: []
              },
              methods: {
                  getLuckySix() {
                      this.myNumbers = _.sampleSize(this.allNumbers, 6)
                      // this.myNumbers.sort((a,b) => a-b)
                      this.myNumbers.sort(function(a,b){
                          return a-b
                      })
                  }
              },
          })
      </script>
  </body>
  ```

* computed

  어떤 함수들을 computed 에 정의하나요? → Data 를 Create Update Delete 하지 않고, Read\(return\) 하는 함수들! \(SQL WHERE\)

  ```jsx
  <!DOCTYPE html>
  <html lang="en">
  <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>VueJS</title>
  </head>
  <body>
    <div id="app">
      <h1>Poor people</h1>
      {{ bankruptPeople }}
    </div>
    <script src="<https://cdn.jsdelivr.net/npm/vue/dist/vue.js>"></script>
    <script>
      const app = new Vue({
        el: '#app',

        data: {
          accounts: [
            { name: 'neo', balance: 500, isBankrupt: true },
            { name: 'tak', balance: 700, isBankrupt: false },
            { name: 'john', balance: 350, isBankrupt: false },
            { name: 'justin', balance: 200, isBankrupt: true },
          ],
        },

        methods: {},

        /*
          어떤 함수들을 computed 에 정의하나요?
          Data 를 Create Update Delete 하지 않고, 
          Read(return) 하는 함수들! (SQL WHERE)
        */ 
        computed: {
          // 함수지만, 이름은 명사형으로 짓는다.
          numOfAccounts: function() {
            return accounts.length
          },

          bankruptPeople: function() {
            // filter 는 새로운 배열을 리턴한다.
            const newArr = this.accounts.filter((account) => {
              return account.isBankrupt
            })
            // filter 가 리턴한 배열을 리턴
            return newArr
          },

        }
      })

    </script>
  </body>
  </html>
  ```

