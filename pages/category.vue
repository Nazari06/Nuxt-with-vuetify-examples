<template>
  <v-row justify="center" align="center" class="mt-3">
    <v-col
      cols="12"
      lg="12"
      sm="12"
      md="12"
    >
      <CategoryComponent />
    </v-col>
  </v-row>
</template>

<script>
import CategoryComponent from '~/components/category/CategoryComponent.vue'
export default {
  name: 'InspirePage',
  components: { CategoryComponent }
}
</script>
