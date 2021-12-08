<template>
  <h1>Baker's Calculator</h1>
  <p>
    Using baker's percentages is a great way to scale any baking recipe. By using
    this formula, you can easily find the necessary amounts of other ingredients
    by how the weight of those ingredients compares to the total amount of flour
    you're using.
  </p>
  <p>
    To really dig into this, I recommend checking out
    <a href="https://www.kingarthurbaking.com/pro/reference/bakers-percentage">this
    super helpful article</a> from King Aruthur.
  </p>
  <p>
    To use the table below, enter the amount of flour in your recipe (by weight), then
    use the percentage fields to get the weight for each of the other ingredients.
  </p>
  <table>
    <thead>
      <tr>
        <th>Ingredient</th>
        <th>Percentage</th>
        <th>Weight</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td><label for="txtFlourWeight">Flour</label></td>
        <td>100%</td>
        <td>
          <input id="txtFlourWeight" v-model="flourWeight" />
        </td>
      </tr>
      <tr>
        <td><label for="txtWaterPercentage">Water</label></td>
        <td><input id="txtWaterPercentage" v-model="waterPercentage" @keyup="calculateWaterWeight" /><span>%</span></td>
        <td><input v-model="waterWeight" /></td>
      </tr>
      <tr>
        <td><label for="txtSaltPercentage">Salt</label></td>
        <td><input id="txtSaltPercentage" v-model="saltPercentage" @keyup="calculateSaltWeight"><span>%</span></td>
        <td><input v-model="saltWeight"></td>
      </tr>
      <tr>
        <td><label for="txtYeastPercentage">Yeast</label></td>
        <td><input id="txtYeastPercentage" v-model="yeastPercentage" @keyup="calculateYeastWeight"><span>%</span></td>
        <td><input v-model="yeastWeight"></td>
      </tr>
    </tbody>
  </table>
</template>

<script>
export default {
  data () {
    return {
      flourWeight: 0,
      waterPercentage: 0,
      waterWeight: 0,
      saltPercentage: 0,
      saltWeight: 0,
      yeastPercentage: 0,
      yeastWeight: 0
    }
  },
  methods: {
    calculateWaterWeight () {
      this.waterWeight = Math.floor((this.waterPercentage / 100) * this.flourWeight)
    },
    calculateSaltWeight () {
      this.saltWeight = Math.floor((this.saltPercentage / 100) * this.flourWeight)
    },
    calculateYeastWeight () {
      this.yeastWeight = Math.floor((this.yeastPercentage / 100) * this.flourWeight)
    }
  }
}
</script>
