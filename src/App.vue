<template>
  <main>
    <form autocomplete="off">
      <label>Список дел</label>
      <br/><br/>
      <input v-model="CurrentTask" type="text">
      <button v-on:click="AddTask()" type="button">Добавить дело</button>
      <button v-on:click="DeleteTask()" type="button">Удалить дело</button>
    </form>
    <section>
      <ol>
        <li v-for="(el, key) in Tasks" v-bind:key="key">
          <span v-if="CurrentTask.length == 0">{{ Error }}</span>
          <span v-else>{{ el.text }}</span>
        </li>
      </ol>
    </section>
  </main>
</template>
<script>
export default {
  data(){
    return{
      CurrentTask: '',
      Error: '',
      Tasks:[
        {
          text: ''
        }
      ]
    }
  },
  methods:{
    AddTask: function(){
      if(this.CurrentTask.length == 0){
        this.Error = "Ошибка! Добавьте дело"
      }
      else{
          this.Tasks.push({
          text: this.CurrentTask
        })
      }
    },
    DeleteTask: function(){
      this.Tasks.pop({
        text: this.CurrentTask
      })
    }
  }
}
</script>
<style scoped>
form{
  margin-left: 5em;
  margin-top: 5em;
}
label, input, button{
  font-size: 3em;
}
button{
  width: 10em;
  height: 2em;
  background-color: #d31ef7;
  color: #ffffff;
  cursor: pointer;
  font-family: 'Open Sans',sans-serif;
  border: 5px solid silver;
  border-radius: 5%;
}
button:hover{
  background-color: #00ff1a;
}
ol{
  margin-left: 4em;
}
</style>