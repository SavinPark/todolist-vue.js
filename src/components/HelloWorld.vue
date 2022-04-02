<template>
  <div class="hello">
	<h1>[ Vue.js 프레임워크 입문 ] 강의 필기 ( 2주차 | 2022.03.26 )</h1>
	<h2>Text</h2>
	<p>{{ msg }}</p> <!-- 보간법 -->
	<p v-text="msg2"></p> <!-- text 바인딩 : 텍스트로 인식 -->
	<p v-html="msg2"></p>  <!-- html 바인딩 : 태그로 인식 -->
    <p>{{ msg.substr(0,6) }}</p> <!-- 보간법 안에 자바스크립트 사용 예 -->
	
	  
	<h2>Array</h2>
	<p>{{ array }}</p> <!-- 배열 -->
	<p>{{ array[1] }}</p> <!-- 배열 안의 요소 -->
	 
	  
	<h2>Object</h2>
	<p>{{ object }}</p> <!-- 객체 -->
	<p>이름은 {{ object.name }}이고, 나이는 {{ object.age }}입니다.</p> <!-- 객체의 속성 1 -->
	<p>{{ "이름은 " + object.name + " 입니다." }}</p> <!-- 객체의 속성 2 -->
	  
	  
	<h2>a Tag</h2>
	<a :href="url">Naver</a> <!-- a태그/href 바인딩 -->
	  
	  
	<h2>Binding</h2>
	<!-- p  v-bind:align="align">{{ msg }}</p -->
	<p :align="align">속성 바인딩 (오른쪽 정렬)</p> <!-- 속성 바인딩 -->
	<p :style="{ backgroundColor: bgcolor}">스타일 바인딩 (배경색)</p> <!-- 스타일 바인딩 -->
	<p :class="className">클래스 바인딩</p> <!-- 클래스 바인딩 -->
	<p :class="flag? 'name' : '' ">클래스 바인딩 - 삼항연산자</p> <!-- 삼항연산자 활용 : flag가 true이면 class명은 name, false이면 class명은 '' -->
	<p :class="flag2">클래스 바인딩 - computed </p> <!-- computed 활용 -->
    
	  
    <h2>v-model 실시간 양방향 바인딩</h2>
	<h3>Input Text</h3>
	<input type="text" v-model='inputText' /> <!-- input (text타입) -->
	<p :class='inputText'>{{ inputText }}</p>
	  
	<h3>Input Radio 버튼</h3>
	<input type="radio" v-model='inputRadio' value="y">라디오 버튼<input/> <!-- input (radio타입) -->
	<p :class="inputRadio=='y' ? 'yellow' : ''"> 안녕하세요 </p>
	  
	<h3>실습) Color btns</h3>
	<input type="radio" v-model='inputRadio' value="g">Green 버튼<input/> <!-- input (radio타입) -->
	<p :class="inputRadio=='g' ? 'green' : ''"> GREEN </p>
	<input type="radio" v-model='inputRadio' value="b">Blue 버튼<input/> <!-- input (radio타입) -->
	<p :class="inputRadio=='b' ? 'blue' : ''"> BLUE </p>
	<input type="radio" v-model='inputRadio' value="r">Red 버튼<input/> <!-- input (radio타입) -->
	<p :class="inputRadio=='r' ? 'red' : ''"> RED </p>
	  
	<h3>Input CheckBox 버튼</h3>
	<input type="checkbox" v-model='inputCheck' value="green">Green 버튼<input/> <!-- input (radio타입) -->
	<input type="checkbox" v-model='inputCheck' value="blue">Blue 버튼<input/> <!-- input (radio타입) -->
	<input type="checkbox" v-model='inputCheck' value="red">Red 버튼<input/> <!-- input (radio타입) -->
	<p> {{ inputCheck }} </p>
	  
	  
	<h2>methods</h2>
	<button @click="hi"> Hi </button>
	<button @click="bye"> Bye </button>
	  
	  
	<h2>Sub 과제) 계산기</h2>
	<input type="text" v-model="num1" />
	<input type="text" v-model="num2" />
	<button @click="plus"> + </button>
	<button @click="minus"> - </button>
	<p> {{ result }} </p>
	  
	  
	<h2>조건문 if - else if - else</h2>
	<p>조건문을 이용하여 화면에 보이고 싶은 부분은 보이도록하고, 숨기고 싶은 부분은 보이지 않도록 조정할 수 있다.</p>
	<p v-if="flag">flag의 값이 true일 경우에만 나옵니다.</p>
	<p v-else-if="flag2">flag의 값은 false, flag2의 값은 true</p>
	<p v-else>flag와 flag2가 모두 flase</p>
	  
	<h2>v-show</h2>
	<p>v-if 와 비슷</p>
	<p>display: none; / hidden 느낌.. 그려져 있지만 화면에 노출만 안되어 있..?</p>
	<p>일반적으로 v-show보다 v-if를 더 많이 사용한다.</p>
	
	<h2>v-for</h2>
	<ul v-for="(food, idx) in menu" :key="idx" @click="select(food.name)"> <!-- :v-for="food in menu" | key를 넣어주는 것을 권장.  v-for="(food, idx) in menu" :key="idx" -->
	  <li>{{ food.name }}의 가격은 {{ food.price }} 원 입니다.</li>
	</ul>
	  
	<h1>[ Vue.js 프레임워크 입문 ] 강의 필기 ( 3주차 | 2022.04.02 )</h1>
	<h2>복습</h2>
	<h4>예제 1 ) 조건문 if</h4>
	  <p v-if='seen'>이제 나를 볼 수 있어요!</p>
	<h4>예제 2 ) 조건문 if-else</h4>
	  <div v-if='Math.random() > 0.5'>
		  이제 나를 볼 수 있어요!
	  </div>
	  <div v-else>
		  이제는 볼 수 없어요ㅠ
	  </div>
	<h4>예제 3 ) 조건문 if-else if-else</h4>
	  <div v-if='type === "A"'>
		  A
	  </div>
	  <div v-else-if='type === "B"'>
	  	  B
	  </div>
	  <div v-else-if='type === "C"'>
		  C
	  </div>
	  <div v-else>
		  Not A/B/C
	  </div>
	<h4>예제 4 ) for문 - 배열</h4>
	  <ul>
		  <li v-for="(item, index) in items" :key="index">
			  {{parentMsg}} - {{index}} - {{item.msg}}
		  </li>
	  </ul>
	<h4>예제 5 ) for문 - 객체</h4>
	  <ul>
		  <li v-for="(value, key, index) in object" :key="key">
			[{{index}}] {{key}} : {{value}}
		  </li>
	  </ul>
	<h4>예제 6 ) v-on:click | @click [메시지 뒤집기]</h4>
	  <p> {{message}} </p>
	  <button v-on:click='reverseMessage'>메시지 뒤집기</button>
	<h4>예제 7 ) v-on:click | @click [카운터]</h4> 
	  <button v-on:click='counter += 1'>Add 1</button>
  	  <p>위 버튼을 클릭한 횟수는  {{counter}}번 입니다.</p>
	<h4>예제 8 ) v-on:click | @click [나이]</h4>
	  <button v-on:click='age -= 1'>- 1</button>
	  <button v-on:click='age += 1'>+ 1</button>
	  <p>{{name}}님의 나이는 {{age}}살 입니다.</p>
	<h4>예제 9 ) computed</h4>
	  <p>원본 메시지 : {{message}}</p>
	  <p>역순으로 표시한 메시지 : {{reverseMessage2}}</p>
	<h4>미니과제 풀이 ) 계산기</h4>
	  <input v-model='a' />
	  <input v-model='b' />
	  <button v-on:click='add'>더하기</button>
	  <button v-on:click='sub'>빼기</button>
	  <p>연산 결과는 {{ result2 }} 입니다.</p>
	<h3>Components</h3>
	<h4>Prop</h4>
	  <button @click='emitCall'>값을 바꿔주세요.</button>
  </div>
</template>

<script>
var code = {name:'박은지', age:'24'};
// v-bind:text="msg2", v-text="msg2" 모두 같은 의미의 명령
export default {
  name: 'HelloWorld',
  props: ['prop'],
  data: function() {
    return { 
		// --------------------------------------------- 2주차
		msg: "Vue.js 수업입니다.",
		msg2: '<h4>반갑습니다 : )</h4>',
		array: ['커피', '자몽차', '레몬차'],
		object: code, // {name:'박은지', age:24}
		url: 'https://www.naver.com',
		align: 'right', // 속성 바인딩
		bgcolor: 'yellow', // 스타일 바인딩
		className: 'name', // 클래스 바인딩 (스타일은 style태그 안에 정의)
		flag: true,
		flag2: false,
		inputText: '',
		inputRadio: '',
		inputCheck: [],
		num1: null,
		num2: null,
		result: null,
	    menu : [
			{name: '피자', price: '23000'},
			{name: '햄버거', price: '10000'},
			{name: '떡볶이', price: '14000'},
		],
		// --------------------------------------------- 3주차
		seen: true,
		type: 'A',
		parentMsg : 'Parent',
		items: [
			{ msg : 'Foo' },
			{ msg : 'Bar' }
		],
		object : {
			title: 'How to do lists in Vue',
			author: 'Jane Doe',
			publishedAt: '2016-04-18'
		},
		message : '안녕하세요 Vue.js!',
		counter : 1,
		name: '박은지',
		age: '24',
		a : 0,
		b : 0,
		result2 : 0,
	}
  },
  computed: {
	  flag2: function() {
		  if(this.msg) return 'name';
	  },
	  // 계산된 getter
	  reverseMessage2: function() {
		  // this는 vm 인스턴스를 가리킨다.
		  return this.message.split('').reverse().join('');
	  },
  },
  methods: {
	  hi: function() { 
		  let result = this.num1 + this.num2;
		  alert("Hello Everyone! 결과는 " + result);
	  },
	  bye: function() { 
		  alert("Bye Everyone!");
	  },
	  plus: function() {
		  this.result = parseInt(this.num1) + parseInt(this.num2);
	  },
	  minus: function() {
		  this.result = parseInt(this.num1) - parseInt(this.num2);
	  },
	  select(param) {
		  alert(param + " 를 주문하시겠어요?");
	  },
	  reverseMessage : function () {
		  //console.log(this.message.split(''));
		  // console.log(this.message.split('').reverse());
		  //console.log(this.message.split('').reverse().join(''));
		  this.message = this.message.split('').reverse().join('');
	  },
	  add : function () {
		 // console.log('add');
		  // 형변환은 Number 혹은 parseInt
		  this.result2 = parseInt(this.a) + parseInt(this.b);
	  },
	  sub : function () {
	  	  //console.log('sub');
		  this.result2 = parseInt(this.a) - parseInt(this.b);
	  },
	  emitCall() {
		  this.$emit('hello', 'b'); // 부모는 hello라는 이름으로 받음
	  }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
a {
  color: #42b983;
}
.name {
	background-color: powderblue;
}
.yellow {
	background-color: yellow;
}
.red {
	background-color: red;
}
.blue {
	background-color: blue;
}
.green {
	background-color: green;
}
</style>
