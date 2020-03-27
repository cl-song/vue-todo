<template>
  <div class="clearAllWrap">
    <button
      type="button"
      @click="clearTodo"
    >
      CLEAR ALL
    </button>
  </div>
</template>

<script>
export default {
    methods: {
        clearTodo() {
            localStorage.clear();
        },
    },
};
</script>

<style scoped>
.clearAllWrap{
    position:fixed;
    bottom:0;
    left:0;
    width:100%;
    background:#eee;
}
button{
    display:block;
    width:100%;
    padding:5px 0;
}
</style>
