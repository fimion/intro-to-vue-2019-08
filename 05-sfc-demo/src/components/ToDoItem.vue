<template>
  <div>
    <h3>
      <label>
        <input type="checkbox"
               @input="toggleCheckBox"
               :checked="complete">
        {{ label }}
      </label>
    </h3>
    <p>{{ description }}</p>
  </div>
</template>

<script>
  export default {
    name: "ToDoItem",
    props:['id','complete', 'label', 'description'],
    methods:{
      toggleCheckBox(e){
        this.$emit('update-complete',
                   {id:this.id,
                    complete:e.target.checked})
      }
    }
  }
</script>

<style scoped>

</style>
