<script>

export default {
  data() {
    return {
      data: []
    }
  },

  mounted() {
    fetch(`https://www.thecocktaildb.com/api/json/v1/1/search.php?s=orange`)
    .then(res => res.json())
    .then(data => this.data = data.drinks)
  },

methods: {
  getData() {

    const searchInput = document.getElementById("search-input").value
    const resultNotify = document.getElementById("result-notify")

    if(searchInput === "") {
      alert("please type fruit name to get search result")
      return;
    }

    fetch(`https://www.thecocktaildb.com/api/json/v1/1/search.php?s=${searchInput}`)
    .then(res => res.json())
    .then(data => this.data = data.drinks)

    resultNotify.innerText = `"${searchInput}"`
    document.getElementById("search-input").value = ""
  },

}

}

</script>

<template>

<div class="drink-wrapper">

  <!-- Spinner Loading -->

  <!-- <div id="spinner" class="flex items-center justify-center">
    <div  class="spinner-border hidden animate-spin w-8 h-8 border-4 rounded-full" role="status">
      <span class="visually-hidden">Loading...</span>
    </div>
  </div> -->

    <div class="search-container w-96 mx-auto">
      <p class="my-6">Search by fruit name like "Apple", Banana, Orange</p>
      <input class="border border-gray-400 px-2 py-2" type="text" id="search-input" placeholder="search">
      <button class="bg-blue-700 text-white px-4 py-2  border border-gray-400" type="submit" @click="getData">Search</button>
      <p class="py-4" >Now showing result for <span id="result-notify">"Orange"</span></p>
    </div>

    <div class="drink-container container mx-auto grid grid-cols-3 gap-3">
      <div class="single-drink-container border border-gray-300 p-2 shadow-lg" v-for="drink in data"
      :key="drink.idDrink"
      >
  
     
          <img v-bind:src="drink.strDrinkThumb" alt="">
          <h2 class="text-2xl mt-3"><span class="font-bold">Name: </span> {{ drink?.strDrink }}</h2>
          <h4 class="text-sm text-slate-800"><span class="font-bold">Category</span> {{ drink?.strCategory }}</h4>
          <p class="text-xs"><span class="font-bold">Details: </span> {{ drink?.strInstructions.slice(0, 150) }}</p>
    </div>


    </div>

</div>

  
</template>
