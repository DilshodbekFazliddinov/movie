<template >
    <ul class="movie-list">
      
        <MoviListItem v-for="movie in movies" v-bind:movie="movie" :key="movie.id"  @onLike = '$emit("onLike" , movie.id)' @onFavourite = '$emit("onFavourite" , movie.id)' @onDelete='$emit("onDelete" , movie.id)' />
        
        
    </ul>
</template>
<script>
import MoviListItem from '../movie-list-item/moviListItem.vue';

export default {
    components:{
        MoviListItem
    },
    props :{
    movies:{
      type:Array,
      Required:true
    }
   }
 
}
</script>
<style scoped>

    .movie-list{
        margin-top: 2rem;
    padding: 1.5rem;
    background-color: #e2e1df9f;
    border-radius: 4px;
    box-shadow: 15px 15px 15px rgba(0,0,0,0.15);
    }
</style>