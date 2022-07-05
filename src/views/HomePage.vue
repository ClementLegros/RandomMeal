<script lang="ts">
import { defineComponent } from "vue";

type Meal = {
  //all the fields from theMealDB
  idMeal: string;
  strMeal: string;
  strCategory: string;
  strArea: string;
  strInstructions: string;
  strMealThumb: string;
  strTags: string;
  strYoutube: string;
  strSource: string;
  dateModified: string;
};

export default defineComponent({
  data() {
    return {
      mealBool: false,
      meal: {} as Meal,
    };
  },
  methods: {
    randomMeal() {
      fetch("https://www.themealdb.com/api/json/v1/1/random.php")
        .then((response) => response.json())
        .then((data) => {
          this.mealBool = true;
          const mealGetted: Meal = data.meals[0];
          this.meal = mealGetted;
        });
    },
  },
});
</script>
<template>
  <div v-if="mealBool">
    <div class="meal">
      <div class="meal-img-container">
        <img
          @click="randomMeal"
          class="meal-img"
          :src="meal.strMealThumb"
          alt="meal"
        />
      </div>
      <div class="meal-info">
        <h1>{{ meal.strMeal }}</h1>
        <p>
          <label class="meal-label">Categories:</label> {{ meal.strCategory }}
        </p>
        <p><label class="meal-label">Origin:</label> {{ meal.strArea }}</p>
        <label class="meal-label">Instructions:</label>
        <p class="meal-instruction">{{ meal.strInstructions }}</p>
      </div>
    </div>
  </div>
  <div v-else class="else-container">
    <button class="rdm-meal-button" @click="randomMeal">
      Get a random meal
    </button>
  </div>
</template>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Inconsolata:wght@200;400&display=swap");
* {
  font-family: "Inconsolata", monospace;
}
.else-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 80vh;
}
.rdm-meal-button {
  background-color: #333;
  color: white;
  border: none;
  border-radius: 5px;
  padding: 10px;
  font-size: large;
  font-family: Verdana, Geneva, Tahoma, sans-serif;
  cursor: pointer;
}
.rdm-meal-button:hover {
  background-color: rgb(200, 70, 70);
}
.meal-img-container {
  padding-top: 5px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 40vh;
}
.meal-img {
  width: 40vh;
}
.meal-info {
  display: flex;
  flex-direction: column;
  align-items: center;
  height: 40vh;
}
.meal-instruction {
  width: 20%;
}

/* for mobile size */
@media screen and (max-width: 600px) {
  .meal {
    height: 100vh;
  }
  .meal-img-container {
    height: 40vh;
  }
  .meal-img {
    width: 39vh;
    object-fit: scale-down;
  }
  .meal-instruction {
    width: 100%;
  }
}
</style>
