<template>
<v-layout wrap>
  <v-flex xs12 sm6>
    <v-layout wrap>
    <v-flex xs12 pa-2 pa-4>
      <v-form>
        <v-layout wrap>
          <v-flex xs12 pa-2>
            <v-text-field
            outlined
              v-model="input_value"
              label="dumbell weight"
              type="number"
            >
            </v-text-field>
          </v-flex>
          <v-flex xs12 pa-2>
            <v-btn dark color="blue" @click="addValues()">Enter</v-btn>
          </v-flex>
          <v-flex xs12 pa-2 v-if="dubell_array"> added values:{{ dubell_array }}</v-flex>
          <v-flex xs12 pa-2> <v-btn @click="countPairs( dubell_array)">
            find pairs
          </v-btn></v-flex>

          <v-flex xs12 pa-2 v-if="pair"> Total pairs: {{ pair }} </v-flex>
        </v-layout>
      </v-form>
    </v-flex>
  </v-layout>
  </v-flex>
</v-layout>
</template>
<script>
export default {
  data() {
    return {
      input_value: null,
      dubell_array: [],
      pair: null,
    };
  },
  methods: {
    addValues() {
      this.dubell_array.push(this.input_value);
      this.input_value = null;
    },
   
    countPairs(arr) {
  const count = {};

  
  for (let i = 0; i < arr.length; i++) {
    const num = arr[i];
    count[num] = (count[num] || 0) + 1;
  }

  
  let pairCount = 0;
  for (const num in count) {
    const occurrences = count[num];
    pairCount += Math.floor(occurrences / 2);
  }

this.pair = pairCount
}

  },
};
</script>