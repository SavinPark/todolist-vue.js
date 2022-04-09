<template>
  <div>
	<main class="todo">
        <div class="container">
			<!-- ul.list_add -->
			<ul class="list_add">
				<li class="list_add_tit"><p>등록 하기</p></li>
				<li><p><input type="text" v-model="addText"><button @click="addTodo">등 록</button></p></li>
			</ul>
   		 <!--// ul.list_add -->
	  </div>
	</main>
  </div>
</template>

<script>
export default {
  name: 'todoInput',
  data : function() {
	  return {
		  addText : '',
	  }
  },
  methods: {
	addTodo() {
	  this.$emit("addTodo", this.addText); // 부모컴포넌트에 this.addText를 "addTodo"라는 이름으로 전달
      this.addText = ""; // 등록 후, 입력칸 초기화
	},
  }
}
</script>
