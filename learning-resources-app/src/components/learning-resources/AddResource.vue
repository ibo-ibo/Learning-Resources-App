<template>
  <base-dialog v-if="inputIsInvalid" title="Invalid Input">
    <template #default>
      <p>Unfortunately, at least one input value is invalid :(</p>
      <p>Please check all inputs and make sure you enter a few characters :)</p>
    </template>
    <template #actions>
      <base-button @click="closeModal">Okay</base-button>
    </template>
  </base-dialog>
  <base-card
    ><form @submit.prevent="submitData">
      <div class="form-control">
        <label for="title">Title</label>
        <input type="text" id="title" name="title" v-model="inputTitle" />
      </div>
      <div class="form-control">
        <label for="description">Description</label>
        <textarea
          type="text"
          id="description"
          name="description"
          rows="3"
          v-model="inputDescription"
        ></textarea>
      </div>
      <div class="form-control">
        <label for="link">Link</label>
        <input
          type="url"
          id="link"
          name="link"
          v-model="inputUrl"
          ref="linkInput"
        />
      </div>
      <div>
        <base-button type="submit">Add</base-button>
      </div>
    </form></base-card
  >
</template>

<script>
export default {
  emits: ['submit-data'],

  data() {
    return {
      a: 'asdlfj',
      inputTitle: '',
      inputDescription: '',
      inputUrl: '',
      inputIsInvalid: false,
    };
  },
  methods: {
    submitData() {
      if (
        this.inputTitle.trim() === '' ||
        this.inputDescription.trim() === '' ||
        this.inputUrl.trim() === ''
      ) {
        this.inputIsInvalid = true;
        console.log('hah');
        return;
      }
      console.log(this.inputTitle);
      this.$emit(
        'submit-data',
        this.inputTitle,
        this.inputDescription,
        this.inputUrl
      );

      this.inputDescription = '';
      this.inputTitle = '';
      this.inputUrl = '';
    },
    closeModal() {
      this.inputIsInvalid = false;
    },
  },
};
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
  padding: 0.15rem;
  border: 1px solid #ccc;
}

input:focus,
textarea:focus {
  outline: none;
  border-color: #3a0061;
  background-color: #f7ebff;
}

.form-control {
  margin: 1rem 0;
}
</style>
