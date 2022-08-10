<template>
  <v-row justify="center" align="center" class="mt-3">
    <v-col
      cols="12"
      lg="12"
      sm="12"
      md="12"
    >
      <v-card>
        <v-card-title
          class="d-inline-block question-card-title mt-3"
        >
          <p class="text--secondary">
            Create question*
          </p>
          <p class="text-sm-body-2 text--secondary">
            You can create one or more question
          </p>
        </v-card-title>
        <v-card-text class=" pl-5">
          <QuestionMain />
        </v-card-text>
      </v-card>
    </v-col>
  </v-row>
</template>

<script>
import QuestionMain from '~/components/question/QuestionMain.vue'
export default {
  name: 'QuestionsPage',
  components: { QuestionMain }
}
</script>

<style scoped>
.question-card-title{
  line-height: 0px !important;
}
</style>
