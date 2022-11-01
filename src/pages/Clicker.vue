<template>
    <div class="columns">
        <div class="column is-one-third has-text-centered">
            <b>{{bears}} clicks</b>
            <br>
            <b>{{cps}} clicks per second</b>  
            <br>
            <br>
            <img @click="bearClick()" :class="{'click': clickClass}" src="https://www.animatedimages.org/data/media/1096/animated-click-here-sign-and-button-image-0042.gif">   
        </div>
        <div class="column" style="width: 100%;">
            <button @click="upgrade(0.1, 10)" class="button is-dark" :disabled="bears<10" style="width: 30%;">Buy 0.1 cps for 10 clicks</button>
            <br> 
            <br> 
            <button @click="upgrade(1, 100)" class="button is-dark" :disabled="bears<100" style="width: 30%;">Buy 1 cps for 100 clicks</button> 
            <br>
            <br>
            <button @click="upgrade(10, 1000)" class="button is-dark" :disabled="bears<1000" style="width: 30%;">Buy 10 cps for 1000 clicks</button> 
            <br>   
            <br>  
            <button @click="upgrade(100, 10000)" class="button is-dark" :disabled="bears<10000" style="width: 30%;">Buy 100 cps for 10000 clicks</button> 
            <br>
            <br>
            <button @click="upgrade(1000, 100000)" class="button is-dark" :disabled="bears<100000" style="width: 30%;">Buy 1000 cps for 100000 clicks</button>
            <br>
            <br>
            <button @click="upgrade(1000, 100000)" class="button is-dark" :disabled="bears<1000000" style="width: 30%;">Buy 10000 cps for 1000000 clicks</button>         
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

b {
    color: darkgrey;
}
</style>