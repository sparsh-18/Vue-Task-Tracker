<template>
<form @submit="addtask" style="padding: 20px; border: 1px solid; margin-bottom: 20px">
  <div class="form-group row">
    <label for="taskName" class="col-sm-3 col-form-label">Task Name</label>
    <div class="col-sm-9">
      <input type="text" class="form-control" v-model="text" id="taskName" placeholder="" required>
    </div>
  </div>
  <div class="form-group row">
    <label for="taskTime" class="col-sm-3 col-form-label">Date and Time</label>
    <div class="col-sm-9">
      <input v-model="day" type="text" class="form-control" id="taskTime" placeholder="">
    </div>
  </div>

  <div class="form-check">
  <input v-model="reminder" class="form-check-input" type="checkbox" value="" id="reminder">
  <label class="form-check-label" for="reminder">
    Reminder
  </label>
</div>
  <button type="submit" style="margin-top: 20px;" class="btn btn-primary" >Submit</button>
</form>

</template>

<script>
export default {
    name: "AddTask",

    data() {
        return {
            id: -1,
            text: "",
            day: "",
            reminder: false
        }
    },

    methods: {
        addtask(e) {
            e.preventDefault()

            const newtask = {
                id: Math.abs(Math.floor(Math.random() * 100000)),
                text: this.text,
                day: this.day,
                reminder: this.reminder
            }
            this.$emit("add-task", newtask)

            this.text = ''
            this.day = ''
            this.reminder = false

        }
    },
    emits : ['add-task']
}

</script>