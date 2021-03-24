<template>
  <div>
    <div class="speechHeader">
      <h1 class="header">Spelling Test</h1>
      <div class="feedbackHeader">
        Number Answered Correctly: {{ activeIndex }} of
        {{ questions.length - 1 }}
      </div>
      <Speech
        :word="questions[activeIndex].word"
        :feedbackActivated="feedbackActivated"
      />
    </div>

    <v-form class="spellingForm">
      <div class="speechContainer">
        <div class="spellingInputContainer">
          <v-text-field
            v-if="feedbackActivated != 3"
            class="spellingInput"
            outlined
            placeholder="Spell The Word You Hear"
            v-model="spellingInput"
          >
          </v-text-field>
        </div>
        <div class="submitButtonContainer">
          <div class="submitButton">
            <v-btn
              v-if="feedbackActivated != 3"
              type="submit"
              color="teal"
              @click.prevent="checkInput()"
              >Submit</v-btn
            >
          </div>
        </div>
      </div>
    </v-form>

    <div class="feedbackFooter">
      <div v-if="feedbackActivated === 3">
        <p>Great job! You've spelled all 10 words correctly!</p>
      </div>
      <div v-if="feedbackActivated === 2">
        <p>That's Correct!</p>
      </div>
      <div v-if="feedbackActivated === 1">
        <p>
          That's Correct! Click the <em>Say Word</em> button again to try the
          next word.
        </p>
      </div>
      <div v-if="feedbackActivated === 0">
        <p></p>
      </div>
      <div v-if="feedbackActivated === -1">
        <p>That's Incorrect. Please try again.</p>
      </div>
    </div>
  </div>
</template>

<script>
import Speech from "./components/Speech.vue";
import data from "./components/PromptsData";

export default {
  components: {
    Speech,
  },

  data() {
    return {
      questions: data,
      activeIndex: 0,
      spellingInput: "",
      feedbackActivated: 0,
    };
  },

  methods: {
    checkInput() {
      if (
        this.questions[this.activeIndex].word.toLowerCase() ===
          this.spellingInput.toLowerCase() &&
        this.activeIndex === 0
      ) {
        this.feedbackActivated = 1;
        this.activeIndex += 1;
        this.spellingInput = "";
      } else if (
        this.questions[this.activeIndex].word.toLowerCase() ===
          this.spellingInput.toLowerCase() &&
        this.activeIndex === 9
      ) {
        this.feedbackActivated = 3;
        this.activeIndex = 0;
        this.spellingInput = "";
      } else if (
        this.questions[this.activeIndex].word.toLowerCase() ===
        this.spellingInput.toLowerCase()
      ) {
        this.feedbackActivated = 2;
        this.activeIndex += 1;
        this.spellingInput = "";
      } else {
        this.feedbackActivated = -1;
      }
    },
  },
};
</script>

<style>
.feedbackFooterContainer {
  display: flex;
  flex-flow: column;
  justify-content: center;
}

.submitButtonContainer {
  display: flex;
  flex-flow: column;
  justify-content: center;
}

.spellingInputContainer {
  margin-top: -3em;
}

.speechHeader {
  display: flex;
  flex-flow: column;
  justify-content: center;
  text-align: center;
  margin: 2em;
}

.spellingInput {
  font-size: 16pt;
  font-weight: 600;
  width: 30em;
}

.header {
  margin-bottom: 0.75em;
}

.header {
  margin-bottom: 0.75em;
}

.submitButton {
  display: flex;
  justify-content: center;
}

.spellingForm {
  display: flex;
  flex-flow: column;
  justify-content: center;
}

.feedbackHeader {
  font-size: 16pt;
  font-weight: 600;
  margin-bottom: 1em;
}

.feedbackFooter {
  display: flex;
  justify-content: center;
  font-size: 16pt;
  font-weight: 600;
  margin-bottom: 1em;
  margin-top: 2em;
}
</style>
