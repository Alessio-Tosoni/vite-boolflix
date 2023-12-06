<script>
import axios from 'axios';
import {store} from './store.js';

import AppHeader from './components/AppHeader.vue'
import SearchBar from './components/SearchBar.vue';
import CardMovies from './components/CardMovies.vue'


export default {
	components: {
		AppHeader,
		SearchBar,
		CardMovies
	},
    data() {
        return {
            store,
			options : {
  			method: 'GET',
  			url: 'https://api.themoviedb.org/3/search/movie',
  			params: {api_key:"ae000a48c3ede78a529a0a8f11fefcb1", query:"", include_adult: 'false', language: 'en-US', page: '1'},
  			headers: {
   			accept: 'application/json',
    		Authorization: 'ae000a48c3ede78a529a0a8f11fefcb1'
  			}
			}

        };
    },
    
	methods: {
		cerca (){
			this.options.params.query = store.searchString
			console.log(this.options.query)
			axios.request(this.options)
			.then(function (response) {
		  console.log(response.data.results);
		  store.movies = response.data.results
			})
			.catch(function (error) {
		  console.error(error);
			})

		}
	}
};

</script>

<template>
    <AppHeader />
	<SearchBar @search="cerca"/>
	<CardMovies v-for="movies in store.movies" :info="movies" />
    
</template>

<style scoped>

</style>