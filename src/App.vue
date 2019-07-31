<template>
  <v-app>
    <v-container fluid px-0>
      <v-checkbox v-model="checkbox" :label="`Checkbox 1: ${checkbox.toString()}`"></v-checkbox>
      <v-radio-group v-model="radioGroup">
        <v-radio v-for="n in 3" :key="n" :label="`Radio ${n}`" :value="n"></v-radio>
      </v-radio-group>
      <v-switch v-model="switch1" :label="`Switch 1: ${switch1.toString()}`"></v-switch>
    </v-container>

    <v-layout justify-center>
      <v-date-picker v-model="picker"></v-date-picker>
    </v-layout>

    <v-form v-model="valid">
      <v-container grid-list-xl>
        <v-layout wrap>
          <v-flex xs12 md4>
            <v-text-field
              v-model="firstname"
              :rules="nameRules"
              :counter="10"
              label="First name"
              required
            ></v-text-field>
          </v-flex>

          <v-flex xs12 md4>
            <v-text-field
              v-model="lastname"
              :rules="nameRules"
              :counter="10"
              label="Last name"
              required
            ></v-text-field>
          </v-flex>

          <v-flex xs12 md4>
            <v-text-field v-model="email" :rules="emailRules" label="E-mail" required></v-text-field>
          </v-flex>
        </v-layout>
      </v-container>
    </v-form>

    <v-container fluid grid-list-xl>
      <v-layout wrap align-center>
        <v-flex xs12 sm6 d-flex>
          <v-select :items="items" label="Standard"></v-select>
        </v-flex>

        <v-flex xs12 sm6 d-flex>
          <v-select :items="items" filled label="Filled style"></v-select>
        </v-flex>

        <v-flex xs12 sm6 d-flex>
          <v-select :items="items" label="Outline style" outlined></v-select>
        </v-flex>

        <v-flex xs12 sm6 d-flex>
          <v-select :items="items" label="Solo field" solo></v-select>
        </v-flex>
      </v-layout>
    </v-container>

    <v-container fluid grid-list-lg>
      <v-layout wrap>
        <v-flex xs12>
          <v-slider
            v-model="volume"
            append-icon="volume_up"
            prepend-icon="volume_down"
            label="Volume"
          ></v-slider>
        </v-flex>
      </v-layout>
    </v-container>
  </v-app>
</template>

<script>
export default {
  name: "App",
  data: () => ({
    checkbox: true,
    radioGroup: 1,
    switch1: true,
    picker: new Date().toISOString().substr(0, 10),
    valid: false,
    firstname: "",
    lastname: "",
    nameRules: [
      v => !!v || "Name is required",
      v => v.length <= 10 || "Name must be less than 10 characters"
    ],
    email: "",
    emailRules: [
      v => !!v || "E-mail is required",
      v => /.+@.+/.test(v) || "E-mail must be valid"
    ],
    items: ["Foo", "Bar", "Fizz", "Buzz"],
    volume: 10
  })
};
</script>
