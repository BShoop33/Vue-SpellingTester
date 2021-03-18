<template>
  <div>
    <v-form>
      <button class="speakButton">
        <img src="speak.jpg" alt="speak" />
        <h3>Say Word</h3>
      </button>
      <v-field
        outlined
        label="Spell The Word You Hear"
        v-model="form.spellingInput"
        ref="spellingInput"
      >
      </v-field>
      <v-btn type="submit" color="teal">Submit</v-btn>
    </v-form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      form: {
        spellingInput: "",
      },
    };
  },
};
</script>

<style>
.speakButton {
  background-color: white;
  cursor: pointer;
}
</style>