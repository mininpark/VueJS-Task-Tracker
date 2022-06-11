<template>
  <form @submit="onSubmit" class="form__add">
    <div class="form__add-control">
      <label for="">Task</label>
      <input 
        type="text" 
        v-model="text" 
        name="text" 
        placeholder="Add Task" />
    </div>
    <div class="form__add-control">
      <label for="">Day & Time</label>
      <input 
        type="text" 
        v-model="day" 
        name="day" 
        placeholder="Add day and time" />
    </div>
    <div class="form__add-control_check">
      <label for="">Set Reminder</label>
      <input 
        type="checkbox" 
        v-model="reminder" 
        name="reminder" />
    </div>

    <input type="submit" value="Save Task" class="btn btn-block">
    
  </form>

</template>

<script>
export default {
  name: 'AddTask',
  data() {
    return {
      text: '',
      day:'',
      reminder: false,
    }
  },
  methods: {
    onSubmit(e) {
      e.preventDefault()

      if(!this.text) {
        alert('Please add a task')
        return
      }

      const newTask = {
        //id: Math.floor(Math.random() * 100000),
        text: this.text,
        day: this.day,
        reminder: this.reminder
      }

      this.$emit('add-task', newTask)

      this.text=''
      this.day=''
      this.reminder=''
    }
  }
}

</script>

<style scoped>
  .form__add {
    display: flex;
    flex-direction: column;
    gap: 0.5rem;
  }
  label {width: 100%;}

  input[type="text"] {
    width: 200%; height: 34px; 
    line-height: 36px;
    padding: 10px;
  }
  .form__add-control {
    display: flex;
    flex-wrap: wrap;
    flex: 1 1;
    justify-content: space-between;
    align-items: space-between;
    margin-bottom: 10px;
}
  .form__add-control_check{
    display: flex;
    align-items: center;
  }
  .form__add-control_check label {
    display: block;
  }
  .form__add-control_check input {
    width: 18px; height: 18px;
    margin-bottom: 6px;
  }
  .btn-block {
    margin-bottom: 20px;
  }

</style>