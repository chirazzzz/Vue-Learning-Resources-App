<template>
  <base-card>
    <form @submit.prevent="submitResource">
      <div class="form-control">
        <label for="title">Title</label>
        <input type="text" name="title" id="title" ref="titleInput" />
      </div>
      <div class="form-control">
        <label for="description">Description</label>
        <textarea name="description" id="description" rows="4" ref="descInput" />
      </div>
      <div class="form-control">
        <label for="link">Title</label>
        <input type="url" name="link" id="link" ref="linkInput" />
      </div>
      <div>
        <base-button type="submit">Add Resource</base-button>
      </div>
    </form>
  </base-card>
  <base-dialog v-if="inputIsInvalid" title="Invalid Input" @close="confirmError">
    <template #default>
      <p>Please enter characters in each input field</p>
    </template>
    <template #actions>
      <base-button @click="confirmError">OK</base-button>
    </template>
  </base-dialog>
</template>

<script>
export default {
  data() {
    return {
      inputIsInvalid: false
    }
  },
  inject: ['addResource'],
  methods: {
    submitResource() {
      const enteredTitle = this.$refs.titleInput.value
      const enteredDesc = this.$refs.descInput.value
      const enteredLink = this.$refs.linkInput.value

      if (enteredTitle.trim() === '' || enteredDesc.trim() === '' || enteredLink.trim() === '') {
        this.inputIsInvalid = true
        return
      }

      this.addResource(this.enteredTitle, this.enteredDesc, this.enteredLink)
    },
    confirmError() {
      this.inputIsInvalid = false
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
