<template>
  <div>
    <h3>
      <label>
        <input type="checkbox"
               @input="toggleCheckBox"
               :checked="item.complete">
        {{ item.title }}
      </label>
    </h3>
    <p>{{ item.description }}</p>
  </div>
</template>

<script>
  export default {
    name: "ToDoItem",
    props:['item'],
    methods:{
      toggleCheckBox(e){
        let result = {...this.item}
        result.complete = e.target.checked
        this.$emit('update-item', result)
      }
    },
  }
</script>

<style scoped>

</style>
