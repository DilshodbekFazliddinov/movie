<template >
   
        
            <li class="d-flex justify-content-between align-center movie-list-item-link "
            :class="[{like:movie.like} , {favourite:movie.favourite}]"
            >
              <span @click="onLike" class="name">{{ movie.name }}</span>
              <input class="number" type="number" name="" id="" v-bind:value="movie.viewers ">
              <div class="d-flex justify-content-center align-items-center">
                <button @click="onFavourite" class="btn btn-cookie btn-sm">
                  <i class="fas fa-cookie"></i>
                </button>
                <button @click="onDelete" class="btn btn-trash btn-sm">
                  <i class="fas fa-trash"></i>
                </button>
                <i class="fas fa-star "></i>
              </div>
            </li>
       
    
</template>
<script>
export default {
   props :{
    movie:{
      type:Object,
      Required:true
    }
   },
   methods:{
    onLike(){
      this. $emit("onLike" , this.movie.id)
      
    },
    onFavourite(){
      this.$emit("onFavourite" , this.movie.id)
      
    },
    onDelete(){
      this.$emit("onDelete" , this.movie.id)
    }
   }
}
</script>
<style scoped>

  .movie-list-item-link{
    list-style: none;
    border-bottom:  2px solid #c9c8c79f;
    padding: 10px 15px;


  }
  
  .movie-list-item-link:last-child{
    border-bottom: none;
  }
  
  .number{
    border: none;
    background-color: transparent;
    outline: none;
    text-align: end;
  }
  .btn-cookie{
    color: rgb(240, 205, 140);
  }
  .btn-trash{
    color: rgba(248, 63, 63, 0.781);
  }
  .fa-star{
    color:rgba(255, 166, 0, 0.74);
    transition: 0.3s all;
    transform: translateX(30px);
    opacity: 0;
  }
  .movie-list-item-link.like .fa-star{
    transform: translateX(0);
    opacity: 1;

  }
  .movie-list-item-link.favourite .name,  .movie-list-item-link.favourite .number{
    color: orange;

  }
</style>