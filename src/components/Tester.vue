<template>
  <div>
    <v-form class="spellingForm">
      <button class="speakButton">
        <img src="speak.jpg" alt="speak" />
        <h3 class="sayWord">Say Word</h3>
      </button>

      <div class="spellingInputContainer">
        <v-text-field
          class="spellingInput"
          outlined
          placeholder="Spell The Word You Hear"
          v-model="form.spellingInput"
          ref="spellingInput"
        >
        </v-text-field>
      </div>
      <div class="submitButtonContainer">
        <v-btn type="submit" class="submitButton" color="teal">Submit</v-btn>
      </div>
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
  align-self: center;
  margin-bottom: 3em;
  width: 15em;
}

.spellingForm {
  display: flex;
  flex-flow: column;
  justify-content: center;
}

.spellingInput {
  font-weight: 800;
  width: 30em;
}

.spellingInputContainer {
  display: flex;
  align-self: center;
}

.submitButton {
  width: 12em;
}

.submitButtonContainer {
  display: flex;
  align-self: center;
}
</style>