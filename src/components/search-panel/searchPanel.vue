<template >
    <div class="searchPanel">
        <form class="form" action="">
            <input class="form-control"  type="search " name="" id="" placeholder="Kinolarni qidirish" @input="changeHandler"  :value="term" >
        </form>
    </div>
</template>
<script>
export default {
    props:{
        updateTermHandler:{
            type:Function,
            Required:true
        }
    },
    data(){
        return {
            term:''
        }
    },
    methods:{
        changeHandler(e){
            this.term = e.target.value,
        this.updateTermHandler(this.term)

        },
    }
}
</script>
<style scoped>

.searchPanel{margin-bottom: 1rem;
}

</style>