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
          <input id="txtFlourWeight" v-model="ingredients[0].totals.weight">
        </td>
      </tr>
      <tr>
        <td><label for="water">Water</label></td>
        <td><input id="water" @keyup="calculateWeight" /><span>%</span></td>
        <td><input v-model="ingredients[1].totals.weight"></td>
      </tr>
      <tr>
        <td><label for="salt">Salt</label></td>
        <td><input id="salt" @keyup="calculateWeight"><span>%</span></td>
        <td><input v-model="ingredients[2].totals.weight"></td>
      </tr>
      <tr>
        <td><label for="yeast">Yeast</label></td>
        <td><input id="yeast" @keyup="calculateWeight"><span>%</span></td>
        <td><input v-model="ingredients[3].totals.weight"></td>
      </tr>
    </tbody>
  </table>
</template>

<script>
export default {
  data () {
    return {
      ingredients: [{
        name: 'flour',
        totals: {
          percentage: 100,
          weight: 0
        }
      }, {
        name: 'water',
        totals: {
          percentage: 0,
          weight: 0
        }
      }, {
        name: 'salt',
        totals: {
          percentage: 0,
          weight: 0
        }
      }, {
        name: 'yeast',
        totals: {
          percentage: 0,
          weight: 0
        }
      }]
    }
  },
  methods: {
    calculateWeight (event) {
      const ingredient = event.target.getAttribute('id')
      const flour = this.ingredients[0].totals.weight

      if (flour) {
        for (const ing of this.ingredients) {
          if (ing.name === ingredient) {
            ing.totals.percentage = event.target.value / 100
            ing.totals.weight = ing.totals.percentage * flour
          }
        }
      }
    }
  }
}
</script>
