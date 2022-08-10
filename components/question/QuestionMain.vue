<template>
  <div>
    <v-stepper
      v-for="(element,index) in elements"
      :key="element.id"
      v-model="e6"
      vertical
      elevation="0"
    >
      <v-stepper-step
        :step="index+1"
         @click="e6=element.id"
         class="text-subtitle-1 stepper-label"
      >
          Question {{ element.id }}
        <v-icon
          small
          color="primary"
          class="close-question-btn"
          @click="removeQuestion(index)"
        >
          mdi-close
        </v-icon>
      </v-stepper-step>

      <v-stepper-content :step="index+1">
        <v-row>
          <v-col
            cols="12"
            lg="6"
            md="6"
            sm="6"
          >
            <p class="ma-0 pb-2 text-subtitle-1">
              Question
            </p>
            <v-text-field
              placeholder="Type..."
              rounded
              dense
              class="question-input"
              prepend-inner-icon="mdi-help-circle"
            />
          </v-col>
          <v-col
            cols="12"
            lg="6"
            md="6"
            sm="6"
          >
            <p class="ma-0 pb-2 text-subtitle-1">
              Type
            </p>
            <v-select
              v-model="element.selectedItem"
              :items="items"
              rounded
              dense
              class="question-input"
              prepend-inner-icon="mdi-lightbulb-on"
              placeholder="Select type"
              @change="showAnswerInputs(index)"
            />
          </v-col>
          <v-col
            v-if="element.showAnswerArea"
            cols="12"
            lg="12"
            md="12"
            sm="12"
            xl="12"
            class="d-inline-block answer-area"
          >
            <p class="ma-0 pb-2 text-subtitle-1">
              Answer
            </p>
            <v-text-field
              v-model="element.answer"
              placeholder="Write answer"
              rounded
              dense
              class="question-input answer-input"
              append-icon="mdi-plus"
              @click:append="addAnswer(index)"
              @keydown.enter="addAnswer(index)"
            />
            <v-row class="chip-row">
              <v-col>
                <v-chip
                  v-for="(a,i) in element.answers"
                  :key="i"
                  class="ma-2 pl-2 pr-2 answer-chip"
                  label
                >
                  <span class="mr-2 rounded-circle answer-number">{{ i+1 }}</span>
                  <span class="answer-text">
                    {{ a }}
                  </span>
                  <v-icon
                    class="ml-3 remove-answer-btn"
                    small
                    color="primary"
                    @click="removeAnswer(i,index)"
                  >
                    mdi-close
                  </v-icon>
                </v-chip>
              </v-col>
            </v-row>
          </v-col>
        </v-row>
      </v-stepper-content>
      <span />
    </v-stepper>
    <v-row class="mt-3">
      <v-col
        cols="12"
        lg="12"
        md="12"
        sm="12"
        xl="12"
        class="add-col"
      >
        <v-icon
          color="primary"
          medium
          class="mr-3 ml-6 add-question-btn"
          @click="addQuestion"
        >
          mdi-plus
        </v-icon>
        <span
          color="text--primary"
          class="add-btn-text"
          @click="addQuestion"
        >
          Add another question
        </span>
      </v-col>
    </v-row>
  </div>
</template>

<script>
export default {
  name: 'QuestionMain',
  data () {
    return {
      e6: 1,
      items: ['Single Choice', 'Multiple Choice'],
      showAnswerArea: false,
      elements: [{id:1, question: '', type: '', answers: [], answer: '', selectedItem: '', showAnswerArea: false }]
    }
  },
 
  methods: {
    addQuestion () {
      this.e6++
      this.elements.push({id:this.e6, question: '', type: '', answers: [], answer: '', selectedItem: '',showAnswerArea: false })
    },
    removeQuestion(i) {
      this.elements.splice(i, 1)
      this.e6--
    },
    showAnswerInputs(i) {
      this.elements[ i ].selectedItem === 'Multiple Choice' ?
        this.elements[ i ].showAnswerArea = true :
        this.elements[ i ].showAnswerArea = false
      this.elements[ i ].selectedItem !== 'Multiple Choice' ?
        this.elements[ i ].answers = [] : ''
    },
    addAnswer (i) {
      this.elements[i].answers.push(this.elements[i].answer)
      this.elements[i].answer = ''
    },
    removeAnswer (i, index) {
      this.elements[index].answers.splice(i, 1)
    }
  }
}
</script>

<style>
.v-stepper__step__step{
  background-color: #1976d2 !important;
  text-align: center !important;
}
.v-stepper__step--active .v-stepper__step__step::after{
  content: '';
  position: absolute;
  border: 1px solid #1976d2 !important;
  width: 34px !important;
  height: 34px !important;
  padding: 10px !important;
  margin-left: 0px !important;
  margin-top: 0px !important;
  border-radius: 50% !important;
}

.add-col{
  margin-top:-20px !important;
  z-index:2 !important;
}
span.chip{
border:1px solid rgb(219, 219, 219) !important;
}
button.remove-answer-btn{
    background-color:transparent;
    margin-right: -5px !important;
}


button.add-question-btn::before{
color:#FFF !important;
font-size: 21px;
}
.add-btn-text{
  margin-top: 10px !important;
  color:#1976d2;
  cursor: pointer;
}
.close-question-btn{
  background-color: transparent !important;
  float: right;
  margin-right: 0px !important;
  font-weight: bold;
}
.close-question-btn::before{
margin-top:-5px;
}
.v-stepper{
  padding-bottom: 0px !important;
}
.v-stepper__step{
  cursor: pointer;
  border-radius: 10px !important;
  padding-left: 26px !important;
  padding-top: 4px !important;
  padding-bottom: 13px !important;
}
.v-stepper__content{
  padding-bottom: 30px !important;
}
div.v-stepper__step--active{
  background-color: #F6FAFE !important;
  padding-top:10px !important;
  padding-bottom:10px !important;
  margin-bottom:10px !important;
}
.v-stepper__step--active .v-stepper__label{
  color: #1976d2 !important;
  text-shadow: none !important;
}
.v-stepper__step--active .v-stepper__content{
  height: fit-content;
}
.v-application--is-ltr .theme--light.v-stepper--vertical .v-stepper__content:not(:last-child){
  border-left:2px solid rgba(0, 0, 0, 0.12);
}
.stepper-label .v-stepper__label{
  color: rgb(0 0 0 / 69%);
  text-shadow: none !important;
}
.question-input{
  height: 41px;
  background-color:#f0f0f0;
  padding-top:6.5px !important;
}
.question-input.v-input--is-focused {
  height: 41px;
  background-color: #FFF !important;
  border: 2px solid lightblue !important;
  color: #1976d2;
  padding-top:6.5px !important;
}
.question-input .v-input__control .v-input__slot .v-input__prepend-inner
{
  margin-left: -10px !important;
}

.answer-input .v-input__control .v-input__slot .v-input__append-inner .v-input__icon .mdi-plus{
  color:#FFF !important;
}
.answer-input .v-input__control .v-input__slot .v-input__append-inner .v-input__icon--append{
  padding-top: 3px !important;
  padding-right: 2px !important;
}
.answer-area{
  margin-top:-7px !important;
}
.answer-number{
    width: 20px;
    height: 20px;
    background-color:rgb(232, 244, 255);
    color: #1976d2;
    font-weight: bold;
    text-align: center;
}

.chip-row{
  margin-top: -5px !important;
}
.answer-chip{
  border: 1px solid #eee !important;
  border-radius: 7px !important;

}
</style>
