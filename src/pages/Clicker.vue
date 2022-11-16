<template>
    <div class="columns">
        <div class="column is-one-third has-text-centered">
            <b>{{stones}} stones</b>
            <br>
            <b>{{cps}} stones per second</b>  
            <br>
            <br>
            <img @click="stoneClick()" :class="{'click': clickClass}" src="https://www.animatedimages.org/data/media/1096/animated-click-here-sign-and-button-image-0042.gif">   
        </div>
        <div class="column" style="width: 100%;">
            <button class="button is-black" style="width: 30%; height: 20%;">CPS SHOP!</button>
            <br> 
            <br> 
            <button @click="upgrade(0.1, 10)" class="button is-dark" :disabled="stones<10" style="width: 30%;">Buy 0.1 cps for 10 stones</button>        
            <br> 
            <br> 
            <button @click="upgrade(1, 100)" class="button is-dark" :disabled="stones<100" style="width: 30%;">Buy 1 cps for 100 stones</button> 
            <br>
            <br>
            <button @click="upgrade2(10, 1000)" class="button is-dark" :disabled="stones<1000" style="width: 30%;">Buy 10 cps for 1000 stones</button> 
            <br>   
            <br>  
            <button @click="upgrade3(100, 10000)" class="button is-dark" :disabled="stones<10000" style="width: 30%;">Buy 100 cps for 10000 stones</button> 
            <br>
            <br>
            <button @click="upgrade4(1000, 100000)" class="button is-dark" :disabled="stones<100000" style="width: 30%;">Buy 1000 cps for 100000 stones</button>
            <br>
            <br>
            <button @click="upgrade5(1000, 100000)" class="button is-dark" :disabled="stones<1000000" style="width: 30%;">Buy 10000 cps for 1000000 stones</button>         
        </div>
    </div>
  
</template> 

<script>
export default {
    created(){
        setInterval(()=>{
            this.stones += this.cps;
            this.stones = parseFloat(this.stones.toFixed(1));

        }, 1000);
    },
    data(){
        return {
            clickClass: false,
            stones: 0,
            cps: 0

        }
    },
    computed: {
        displaystones(){
            return parseFloat(this.stones.toFixed(1));
        },
        displayCps(){
            return parseFloat(this.cps.toFixed(1));
        },
    },
    methods: {
        stoneClick(){
            this.stones++;
            this.clickClass = true;
            setTimeout(()=> {
                this.clickClass = false;
            }, 100);
        },
        upgrade(cps, cost){
            if(this.stones >= cost){
                this.stones -= cost;
                alert(`Would you like to upgrade?`);
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