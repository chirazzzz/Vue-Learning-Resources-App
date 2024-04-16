<template>
  <base-card>
    <form @submit.prevent="submitResource">
      <div class="form-control">
        <label for="title">Title</label>
        <input type="text" name="title" id="title" v-model="enteredTitle" />
      </div>
      <div class="form-control">
        <label for="description">Description</label>
        <textarea name="description" id="description" rows="4" v-model="enteredDesc" />
      </div>
      <div class="form-control">
        <label for="link">Title</label>
        <input type="url" name="link" id="link" v-model="enteredLink" />
      </div>
      <div>
        <base-button type="submit">Add Resource</base-button>
      </div>
    </form>
  </base-card>
</template>

<script>
export default {
  emits: ['new-resource'],
  data() {
    return {
      enteredTitle: '',
      enteredDesc: '',
      enteredLink: ''
    }
  },
  methods: {
    submitResource() {
      this.$emit('new-resource', this.enteredTitle, this.enteredDesc, this.enteredLink)
    }
  }
}
</script>

<style scoped>
label {
  font-weight: bold;
  display: block;
  margin-bottom: 0.5rem;
}

input,
textarea {
  display: block;
  width: 100%;
  font: inherit;
  padding: 0.15eem;
  border: 1px solid #ccc;
}

input:focus,
textarea:focus {
  outline: none;
  border-color: #3a0061;
  background-color: #f7ebff;
}

.form-control {
  margin: 1em 0;
}
</style>
