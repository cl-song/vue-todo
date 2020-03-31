<template>
  <ul class="todoList">
    <li
      v-for="(todoItem, index) in propsdata"
      :key="todoItem"
    >
      <span>
        {{ todoItem }}
      </span>
      <button
        type="button"
        class="btnDel"
        @click="removeTodo(todoItem, index)"
      >
        <span class="blind">삭제</span>
      </button>
    </li>
  </ul>
</template>

<script>
export default {
    // eslint-disable-next-line vue/require-prop-types
    props: ['propsdata'],
    methods: {
        removeTodo(todoItem, index) {
            this.$emit('removeTodo', todoItem, index);
        },
    },
};
</script>

<style>
.todoList li{
    position:relative;
    box-sizing:border-box;
    display:table;
    width:calc(100% - 20px);
    min-height:30px;
    margin:10px;
    padding:5px 40px 5px 5px;
    background:#d5d4fb;
    border-radius:10px;
}
.todoList li > span{
    display:table-cell;
    vertical-align:middle;
}
.btnDel{
    position:absolute;
    top:50%;
    right:10px;
    display:inline-block;
    width:20px;
    height:20px;
    background:#f3f3f3;
    border-radius:10px;
    vertical-align:middle;
    transform:translateY(-50%);
}
.btnDel:before,
.btnDel:after{
    content:'';
    position:absolute;
    top:50%;
    left:50%;
    display:inline-block;
    width:10px;
    height:1px;
    background:#333;
    transform:translate(-50%, -50%) rotate(45deg);
}
.btnDel:after{
    transform:translate(-50%, -50%) rotate(135deg);
}
</style>
