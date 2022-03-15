<template>
  <div>
    <b-form @submit="onSubmit" @reset="onReset">
      <b-form-group
          id="input-group-1"
          label="Name"
          label-for="input-1"
      >
        <b-form-input
            id="input-1"
            v-model="form.name"
            type="text"
            placeholder="Enter name"
            required
        ></b-form-input>
      </b-form-group> 
      <b-form-group
          id="input-group-1"
          label="Job"
          label-for="input-1"
      >
        <b-form-input
            id="input-1"
            v-model="form.job"
            type="text"
            placeholder="Enter job"
            required
        ></b-form-input>
      </b-form-group>

      <b-button type="submit" variant="primary">Submit</b-button>
      <b-button type="reset" variant="danger">Reset</b-button>
    </b-form>
    <b-card class="mt-3" header="Form Data Result">
      <pre class="m-0">{{ form }}</pre>
    </b-card>
  </div>
</template>

<script>
const axios = require('axios');
export default {
  data() {
    return {
      form: {
        name: '',
        job: '',
      },
    }
  },
  methods: {
    onSubmit(event) {
      event.preventDefault()
      // alert(JSON.stringify(this.form))
      axios.post('https://reqres.in/api/users',this.form).then(
          ({data})=>{
            alert(JSON.stringify(data))
          }
      )
    },
    onReset(event) {
      event.preventDefault()
      // Reset our form values
      this.form.name = ''
      this.form.job = ''
      // Trick to reset/clear native browser form validation state
      this.show = false
      this.$nextTick(() => {
        this.show = true
      })
    }
  }
}
</script>