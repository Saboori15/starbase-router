<template>
    <div class="col-md-12">
        <Item
        v-for="(item,index) in items"
        :key="index"
        :item="item"
        :type="type"
        />
    </div>
</template>
<script>
import Item from './Item.vue'
export default {
    data(){
        return{
            type: this.$route.params.type,
            items:[]
        }
    },
    watch:{
        '$route':'fetchItems'
    },
    methods:{
        fetchItems(){
            
            this.items=[]
            this.type=this.$route.params.type
            let initialIds=[1,4,14]
            for (let i in initialIds){
                let id=initialIds[i]
                console.log(id)
                fetch(`http://swapi.dev/api/${this.type}/${id}`,
                {
          method:'GET'
        }).then(response=>response.json()).then(json=>this.items.push(json))
            }

        },


        
    },
    components:{
        Item
    }

}
</script>