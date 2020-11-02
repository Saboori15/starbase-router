<template>
<div class="col-md-4" @click="switchItems">
    <div class="item-card">
        <div class="card-block">
            <h4 class="card-title">{{item.name}}</h4>
            <div v-for="(value,key,index) in item"
             :key="index"
                     >
                <div v-if="index < 5">
                    <strong>{{key}}</strong>:{{value}}
                        
                </div>

            </div>

            </div>

        </div>
    </div>
    
</template>
<script>
export default {
    props:['item','type'],
    methods:{
        switchItems(){
            console.log("hello")
            let random_id=Math.floor(Math.random()*63)+1
             fetch(`http://swapi.dev/api/${this.type}/${random_id}`,
                {
          method:'GET'
        }).then(response=>response.json()).then(json=>this.item=json)
        }

    }
}
</script>