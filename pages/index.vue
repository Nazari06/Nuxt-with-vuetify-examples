<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="12" md="12" lg="12">
      <AttributeInsertions />
    </v-col>
  </v-row>
</template>

<script>
import AttributeInsertions from '~/components/AttributeInsertions.vue'
export default {
  name: 'IndexPage',
  components: { AttributeInsertions }
}
</script>
