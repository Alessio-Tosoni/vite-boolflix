<script>
export default {
    name: "CardMovies",
    props: {
        info: Object
    },
    data (){
        return {
            imageName:""
        };
    },
    methods:{
        getImagePath: function(img) {
            return new URL(`../assets/${img}.png`, import.meta.url).href;
        }
    }
}
</script>

<template>
    <div class="card-wrapper">
        <div class="card">
            <div>
                <p class="mt-8">{{ info.title }}</p>
                <p class="mt-8">{{ info.original_title }}</p> 
                <img class="mt-8" :src="getImagePath(info.original_language)">
                <p class="mt-8">{{ info.vote_average }}</p>
                

            </div>
        </div>
    </div>
</template>

<style scoped>
.card-wrapper {
    padding: 1rem;
    width: calc(100% / 4);
}

.card {
    padding: 1rem;
    background-color: #eee;
    color: black;
}
</style>