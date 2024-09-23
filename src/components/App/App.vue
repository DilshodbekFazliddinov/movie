<template>
 
<div class="app">
  <div class="content">
     <AppInfo :AppInfoCounts= "movies.length" :favouriteMoviesCount="movies.filter(a => a.favourite).length"/> 
      <div class="search-panel">
        <SearchPanle :updateTermHandler = 'updateTermHandler'/>
        <AppFilter/>
      </div>
      <div class="movie_List">
        <MovieList :movies="onSearchHandler(movies , term)" @onLike = 'onLikeHandler' @onFavourite = 'onFavouriteHandler' @onDelete = 'onDeleteHandler'  />
      </div>
      <div class="addNewMovie">
        <AddNewMOvie @createMovie="createMovie"/>
      </div>
    
    </div>
</div>
</template>
<script>
  import AppInfo from "@/components/app-info/appInfo.vue";
  import SearchPanle from "@/components/search-panel/searchPanel.vue"

  import MovieList from "@/components/movie-list/movieList.vue";
import AppFilter from "../appFilter/appFilter.vue";
import AddNewMOvie from "../add-new-movie/addNewMOvie.vue";
  export default {
    components:{
      AppInfo,
      SearchPanle,
      AppFilter,
      MovieList,
      AddNewMOvie,
    }, 
    data () {
        return {
            movies :[

            {
                name:'Chuqur',
                viewers:'1500',
                like:true,
                favourite:true,
                id :1
            },
            {
                name:'Ichkarida',
                viewers:450,
                like:false,
                favourite:true,
                id :2


            },
            {
                name:'Ertugrul',
                viewers:450,
                like:false,
                favourite:false,
                id :3


            }
            ],
              term  :'',

        }
    },
    methods:{
      createMovie(item) {
        this.movies.push(item)
        console.log(item);
        
      }, 
      onLikeHandler(id){
       this.movies.map(item =>{
        if(item.id == id){
          item.like = !item.like
        }
        return item
        
       })
              },
      onFavouriteHandler(id){
        this.movies.map(item =>{
          if(item.id == id ){
            item.favourite = !item.favourite
          }
          return item
        })
        
        },
        onDeleteHandler(id){
          this.movies = this.movies.filter(c => c.id !== id )
          console.log(id);
          
        },
        onSearchHandler(arr, term){
          if (term.length == 0){
            return arr
          }
          return arr.filter(c => c.name.toLowerCase().indexOf(term) > -1)
        },
        updateTermHandler(term){
          this.term = term
        }
    }
  }

</script>
<style>
  .app{
    height: 100vh;
    color: #000;
 
  }
  .content{
    width: 1000px;
    min-height: 700px;
    margin: 0 auto;
    background-color: #fff;
    padding: 5rem 0;
  }
  .search-panel{
    margin-top: 2rem;
    padding: 1.5rem;
    background-color: #e2e1df9f;
    border-radius: 4px;
    box-shadow: 15px 15px 15px rgba(0,0,0,0.15);
}
  
 
  

</style>