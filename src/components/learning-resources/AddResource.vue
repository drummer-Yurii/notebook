<template>
    <BaseDialog v-if="inpuIsInvalid" title="Invalid Input" @close="confirmError">
        <template #default>
            <p>Unfortunately at list one input in invalid</p>
            <p>Please check all inputs and make sure you enter at list one character into each input field</p>
        </template>
        <template #actions>
            <BaseButton @click="confirmError">Okey</BaseButton>
        </template>
    </BaseDialog>
  <BaseCard>
    <form @submit.prevent="submitData">
      <div class="form-control">
        <label for="title">Title</label>
        <input id="title" name="title" type="text" ref="titleInput" />
      </div>
      <div class="form-control">
        <label for="description">Description</label>
        <textarea name="description" id="description" rows="3" ref="descInput"></textarea>
      </div>
      <div class="form-control">
        <label for="link">Link</label>
        <input id="link" name="link" type="url" ref="linkInput" />
      </div>
      <div>
        <BaseButton type="submit">Add Resource</BaseButton>
      </div>
    </form>
  </BaseCard>
</template>

<script>
import BaseDialog from '../UI/BaseDialog'
import BaseButton from '../UI/BaseButton';
import BaseCard from '../UI/BaseCard';
export default {
  components: {
    BaseDialog,
    BaseButton,
    BaseCard,
  },
  name: 'AddResource',
  inject: ['addNote'],
  data() {
    return {
      inpuIsInvalid: false,
    };
  },
  methods: {
    submitData() {
      const enteredTitle = this.$refs.titleInput.value;
      const enteredDescription = this.$refs.descInput.value;
      const enteredLink = this.$refs.linkInput.value;

      if (
        enteredTitle.trim() === '' ||
        enteredDescription.trim() === '' ||
        enteredLink.trim() === ''
      ) {
        this.inpuIsInvalid = true;
        return;
      }

      this.addNote(enteredTitle, enteredDescription, enteredLink);
    },
    confirmError() {
        this.inpuIsInvalid = false
    }
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
