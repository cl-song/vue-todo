<template>
  <div class="inputWrap">
    <input
      v-model="newTodoItem"
      type="text"
      placeholder="Type what you have to do"
      @keyup.enter="addTodo"
    >
    <button
      type="button"
      @click="addTodo"
    >
      <span class="blind">
        추가
      </span>
    </button>
  </div>
</template>

<script>
export default {
    data() {
        return {
            newTodoItem: '',
        };
    },
    methods: {
        addTodo() {
            if (this.newTodoItem !== '') {
                // 인풋박스에 입력된 테스트의 앞뒤 공백 문자열 제거
                // eslint-disable-next-line no-unused-vars
                const value = this.newTodoItem && this.newTodoItem.trim();
                localStorage.setItem(this.newTodoItem, this.newTodoItem);
                this.clearInput();
            }
        },
        clearInput() {
            this.newTodoItem = '';
        },
    },
};
</script>

<style scoped>
.inputWrap{
    position:relative;
}
input[type="text"]{
    width:100%;
    height:60px;
    padding:0 60px 0 10px;
    border:0;
    border-bottom:1px solid #ddd;
}
button{
    position:absolute;
    top:50%;
    right:10px;
    display:inline-block;
    width:40px;
    height:40px;
    background:#ead4fb;
    border-radius:10px;
    transform:translateY(-50%);
}
button:before{
    content:'+';
    font-size:24px;
    font-weight:500;
}
</style>
