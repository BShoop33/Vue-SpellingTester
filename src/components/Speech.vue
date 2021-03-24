
<template>
  <div>
    <v-form v-if="feedbackActivated != 3">
      <button @click.prevent="speak()" class="speakButton">
        <img src="speak.jpg" alt="speak" />
        <h3 class="sayWord">Say Word</h3>
      </button>
    </v-form>
  </div>
</template> 

<script>
export default {
  props: ["word", "feedbackActivated"],

  data() {
    return {};
  },
  methods: {
    speak() {
      const utterance = new SpeechSynthesisUtterance(this.word);
      speechSynthesis.speak(utterance);
    },
  },
};
</script>

<style>
.speechContainer {
  display: flex;
  flex-flow: column;
  justify-content: center;
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

.speakButton {
  background-color: white;
  cursor: pointer;
  align-self: center;
  border-radius: 10px;
  margin-bottom: 3em;
  width: 15em;
  border: 2px;
  border-color: black;
  border-style: solid;
}

.speakButton:hover {
  color: blue;
  cursor: pointer;
  align-self: center;
  margin-bottom: 3em;
  width: 15em;
  border: 2px;
  border-radius: 10px;
  border-color: blue;
  border-style: solid;
}

.speakerButton:c {
  color: orange;
}
</style>