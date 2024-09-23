<template >
    <div class="form_movie ">
        <h1 >Yangi kino qo'shish</h1>
        <form class="form form-group d-flex" @submit.prevent>
            <input class="form-control" type="search" name="" id="" placeholder="Qanday kino?" :value="name" @input="name=$event.target.value">
            <input class="form-control" type="number" name="" id="" placeholder="Necha marotaba ko'rilgan?" :value="viewers" @input="viewers=$event.target.value">
            <button class="btn btn-outline-dark" type="submit" @click="addMovie">Qo'shish</button>
        </form>
    </div>
</template>
<script>
export default {
  
    data(){
        return{
            name:'',
            viewers:''
        }
    },
    methods :{
        addMovie(){
            if(!this.name || !this.viewers) return
            const newMovie = {
                name:this.name,
                viewers:this.viewers,
                like:false,
                favourite:false,
                id:Date.now()
            }
            
            this.$emit("createMovie" , newMovie),
            this.name= "",
            this.viewers= ""
            
        }
    }
   
}
</script>
<style scoped>
    .form_movie{
        margin-top: 2rem;
    padding: 1.5rem;
    background-color: #e2e1df9f;
    border-radius: 4px;
    box-shadow: 15px 15px 15px rgba(0,0,0,0.15);
    }
</style>