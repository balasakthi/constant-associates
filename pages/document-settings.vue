<template>
  <v-container class="pa-6 pa-md-12">
    <v-card title="Document Settings" rounded="lg">
      <v-card-item class="mx-4">
        <v-row class="pa-2">
          <v-col cols="12" md="6" lg="3">
            <v-text-field
              color="primary"
              label="Title"
              variant="outlined"
            ></v-text-field>
            <v-text-field
              color="primary"
              label="Author"
              variant="outlined"
            ></v-text-field>
            <v-number-input
              color="primary"
              :reverse="false"
              controlVariant="default"
              label="Margin Top"
              :hideInput="false"
              :inset="false"
              variant="outlined"
            ></v-number-input>
          </v-col>
          <v-col cols="12" md="6" lg="3">
            <v-number-input
              color="primary"
              :reverse="false"
              controlVariant="default"
              label="Margin Left"
              :hideInput="false"
              :inset="false"
              variant="outlined"
            ></v-number-input>
            <v-number-input
              color="primary"
              :reverse="false"
              controlVariant="default"
              label="Margin Bottom"
              :hideInput="false"
              :inset="false"
              variant="outlined"
            ></v-number-input>

            <v-number-input
              color="primary"
              :reverse="false"
              controlVariant="default"
              label="Margin Right"
              :hideInput="false"
              :inset="false"
              variant="outlined"
            ></v-number-input>
          </v-col>
          <v-col cols="12" md="6" lg="3">
            <v-autocomplete
              color="primary"
              label="Font"
              :items="['Arial', 'Times New Roman']"
              variant="outlined"
            ></v-autocomplete>

            <v-number-input
              color="primary"
              :reverse="false"
              controlVariant="default"
              label="Font Size"
              :hideInput="false"
              :inset="false"
              variant="outlined"
            ></v-number-input>

            <v-autocomplete
              color="primary"
              label="Language"
              :items="['English(US)', 'English(UK)', 'French']"
              variant="outlined"
            ></v-autocomplete>
            <v-autocomplete
              color="primary"
              label="Orientation"
              :items="['Portrait', 'Vertical']"
              variant="outlined"
            ></v-autocomplete>
          </v-col>
          <v-col cols="12" md="6" lg="3">
            <v-autocomplete
              color="primary"
              label="Paper Size"
              :items="['A4', 'A3', 'Letter']"
              variant="outlined"
            ></v-autocomplete>

            <v-dialog max-width="350">
              <template v-slot:activator="{ props: activatorProps }">
                <v-btn
                  class="text-none"
                  color="primary"
                  flat
                  v-bind="activatorProps"
                  text="Background Color"
                ></v-btn>
              </template>

              <template v-slot:default="{ isActive }">
                <v-card title="Background Color">
                  <v-card-text>
                    <v-color-picker></v-color-picker>
                  </v-card-text>

                  <v-card-actions>
                    <v-spacer></v-spacer>

                    <v-btn
                      class="text-none"
                      text="Okay"
                      @click="isActive.value = false"
                    ></v-btn>
                  </v-card-actions>
                </v-card>
              </template>
            </v-dialog>

            <v-checkbox
              label="Password Protected?"
              color="primary"
            ></v-checkbox>
            <v-text-field
              color="primary"
              label="Password"
              variant="outlined"
              type="password"
            ></v-text-field>
          </v-col>
        </v-row> </v-card-item
    ></v-card>

    <v-card class="mt-16" title="Watermark Settings" rounded="lg">
      <v-card-item class="mx-4">
        <v-row class="pa-2">
          <v-col cols="12" md="6" lg="4">
            <v-text-field
              color="primary"
              label="Watermark Text"
              variant="outlined"
            ></v-text-field>
            <v-number-input
              color="primary"
              :reverse="false"
              controlVariant="default"
              label="Font Size"
              :hideInput="false"
              :inset="false"
              variant="outlined"
            ></v-number-input>
          </v-col>
          <v-col cols="12" md="6" lg="4">
            <v-autocomplete
              color="primary"
              label="Watermark position"
              :items="['Straight', 'Diagonal']"
              variant="outlined"
            ></v-autocomplete>

            <v-autocomplete
              color="primary"
              label="Watermark Font"
              :items="['Arial', 'Times New Roman']"
              variant="outlined"
            ></v-autocomplete>
          </v-col>
          <v-col cols="12" md="6" lg="4">
            <v-dialog max-width="350">
              <template v-slot:activator="{ props: activatorProps }">
                <v-btn
                  class="text-none"
                  color="error"
                  flat
                  v-bind="activatorProps"
                  text="Font Color"
                ></v-btn>
              </template>

              <template v-slot:default="{ isActive }">
                <v-card title="Font Color">
                  <v-card-text>
                    <v-color-picker></v-color-picker>
                  </v-card-text>

                  <v-card-actions>
                    <v-spacer></v-spacer>

                    <v-btn
                      class="text-none"
                      text="Okay"
                      @click="isActive.value = false"
                    ></v-btn>
                  </v-card-actions>
                </v-card>
              </template>
            </v-dialog>

            <v-checkbox label="Semi Trasparent?" color="primary"></v-checkbox>
          </v-col>
        </v-row>

        <v-card-actions>
          <v-btn class="text-none me-4" color="primary" variant="tonal"
            >Save</v-btn
          >

          <v-btn class="text-none" color="error" variant="tonal">Cancel</v-btn>
        </v-card-actions>
      </v-card-item></v-card
    ></v-container
  >
</template>

<script setup>
import { ref } from "vue";
</script>
