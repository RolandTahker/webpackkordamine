<template>
    <div class="columns">
        <div class="column is-one-third has-text-centered">
            <b>{{bears}} bears</b>
            <br>
            <b>{{cps}} bears per second</b>  
            <img @click="bearClick()" :class="{'click': clickClass}" src="https://placebear.com/800/600">   
        </div>
        <div class="column">
            <button @click="upgrade(0.1, 10)" class="button is-primary" :disabled="bears<10">Buy 0.1 cps for 10 bears</button>     
            <button @click="upgrade(1, 100)" class="button is-primary" :disabled="bears<100">Buy 1 cps for 100 bears</button> 
            <button @click="upgrade(10, 1000)" class="button is-primary" :disabled="bears<1000">Buy 10 cps for 1000 bears</button>      
            <button @click="upgrade(100, 10000)" class="button is-primary" :disabled="bears<10000">Buy 100 cps for 10000 bears</button> 
            <button @click="upgrade(1000, 100000)" class="button is-primary" :disabled="bears<100000">Buy 1000 cps for 100000 bears</button>         
        </div>
    </div>
  
</template> 

<script>
export default {
    created(){
        setInterval(()=>{
            this.bears += this.cps;
            this.bears = parseFloat(this.bears.toFixed(1));

        }, 1000);
    },
    data(){
        return {
            clickClass: false,
            bears: 0,
            cps: 0

        }
    },
    computed: {
        displayBears(){
            return parseFloat(this.bears.toFixed(1));
        },
        displayCps(){
            return parseFloat(this.cps.toFixed(1));
        },
    },
    methods: {
        bearClick(){
            this.bears++;
            this.clickClass = true;
            setTimeout(()=> {
                this.clickClass = false;
            }, 100);
        },
        upgrade(cps, cost){
            if(this.bears >= cost){
                this.bears -= cost;
                this.cps += cps;
            }
        }
    }

}
</script>

<style scoped>
    img.click {
        transform: scale(0.9);
    }

</style>