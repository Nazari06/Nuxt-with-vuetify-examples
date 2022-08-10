<template>
  <v-card elevation="0" outlined class="col-lg-4 col-md-4 col-sm-4 ma-3">
    <v-container>
      <v-card-header>
        <div class="text--secondary">
          Attribute 1
        </div>
      </v-card-header>
      <v-card-text class="d-inline-block mt-2">
        <div class="text--secondary">
          Attribute Name
        </div>
        <v-text-field
          placeholder="Name"
          filled
          class="w-full"
          rounded
          dense
        />
        <div class="text--secondary">
          Attribute Value
        </div>
        <v-text-field
          placeholder="Value"
          filled
          rounded
          dense
          append-icon="mdi-plus"
          @click:append="addValue"
        />
        <v-row class="d-flex">
          <v-chip
            class="pr-6 ma-1"
            close
            color="secondary darken-3"
            outlined
          >
            New value Available
          </v-chip>
          <v-chip
            class="pr-6  ma-1"
            close
            color="secondary darken-3"
            outlined
          >
            Second
          </v-chip>
          <v-chip
            class="pr-6  ma-1"
            close
            color="secondary darken-3"
            outlined
          >
            another value
          </v-chip>
          <v-chip
            class="pr-6  ma-1"
            close
            color="secondary darken-3"
            outlined
          >
            Test value
          </v-chip>
          <v-chip
            class="pr-6  ma-1"
            close
            color="secondary darken-3"
            outlined
            @click:close="removeValue"
          >
            val
          </v-chip>
        </v-row>
      </v-card-text>
    </v-container>
  </v-card>
</template>

<script>
export default {

  name: 'FormComponent'
}
</script>
