<template>
  <div class="add-smoothie container">
    <h2 class="center-align indigo-text">Add new Smoothie recipe</h2>
    <form action @submit.prevent="AddSmoothie">
      <div class="field title">
        <label for="title">Smoothie title:</label>
        <input type="text" name="title" v-model="title" />
        <div v-for="(ing, index) in ingredients" :key="index">
          <label for="ingredient">Ingredient:</label>
          <input type="text" name="ingredient" id v-model="ingredients[index]" />
        </div>
        <div class="field add-ingredient">
          <label for="add-ingredients">Add an ingredient</label>
          <input type="text" name="add-ingredient" @keydown.tab.prevent="AddIng" v-model="another" />
        </div>
        <div class="field center-align">
          <p v-if="feedback" class="red-text">{{ feedback }}</p>
          <button class="btn pink">Add smoothie</button>
        </div>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  name: "AddSmoothie",
  data() {
    return {
      title: null,
      another: null,
      ingredients: [],
      feedback: null
    };
  },
  methods: {
    AddSmoothie() {
      console.log(this.title, this.ingredients);
    },
    AddIng() {
      if (this.another) {
        this.ingredients.push(this.another);
        this.another = null;
        this.feedback = null;
      } else {
        this.feedback = "You must enter a valid value to add an ingredient";
      }
    }
  }
};
</script>

<style>
.add-smoothie {
  margin-top: 60px;
  padding: 20px;
  max-width: 500px;
}
.add-smoothie h2 {
  font-size: 2em;
  margin: 20px auto;
}

.add-smoothie .field {
  margin: 20px auto;
}
</style>
