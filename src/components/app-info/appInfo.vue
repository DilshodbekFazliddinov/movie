<template>

    <div class="appInfo">
        <p>Barcha kinolar soni:{{ AppInfoCounts }}</p>
        <p>Ko'rilgan kinolar soni:{{ favouriteMoviesCount }}</p>
    </div>
</template>
<script>
 export default {
    props:{
        AppInfoCounts:{
            type:Number,
            Required:true
        },
        favouriteMoviesCount:{
            type:Number,
            Required:true
        }
    }
}
</script>
<style>
.appInfo{
    margin-top: 2rem;
    padding: 1.5rem;
    background-color: #e2e1df9f;
    border-radius: 4px;
    box-shadow: 15px 15px 15px rgba(0,0,0,0.15);
    font-size: 30px ;
}</style>