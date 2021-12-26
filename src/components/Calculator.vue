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
      <tr v-for="ingredient in this.ingredients" :key="ingredient.name">
        <td>
          <span v-if="ingredient.name">
            {{ ingredient.name }}
          </span>
          <input v-else type="text">
        </td>
        <td>
          <span v-if="ingredient.name.toLowerCase() ==='flour'">100</span>
          <input v-else v-model="ingredient.totals.percentage" @keyup="calculateWeight(ingredient)">%
        </td>
        <td>
          <input v-if="ingredient.name.toLowerCase() ==='flour'" type="text" v-model="ingredient.totals.weight">
          <span v-else>{{ ingredient.totals.weight }}</span>
        </td>
      </tr>
    </tbody>
  </table>
  <button @click="addIngredient">Add an ingredient</button>
</template>

<script>
export default {
  data () {
    return {
      ingredients: [{
        name: 'Flour',
        totals: {
          percentage: 100,
          weight: 0
        }
      }, {
        name: 'Water',
        totals: {
          percentage: 0,
          weight: 0
        }
      }, {
        name: 'Salt',
        totals: {
          percentage: 0,
          weight: 0
        }
      }, {
        name: 'Yeast',
        totals: {
          percentage: 0,
          weight: 0
        }
      }]
    }
  },
  methods: {
    calculateWeight (el) {
      const flour = this.ingredients[0].totals.weight

      if (flour) {
        el.totals.weight = (el.totals.percentage / 100) * flour
      }
    },
    addIngredient () {
      this.ingredients.push({ name: '', totals: { percentage: 0, weight: 0 } })
    }
  }
}
</script>
