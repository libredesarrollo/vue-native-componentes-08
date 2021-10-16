<template>
    <view :style="{ marginTop:15, marginLeft:'auto', marginRight: 'auto', width:'90%' }">
        <touchable-opacity  :style="[ type == 'sm' ? { alignSelf:'center' } : {} ]" :class="[background]" class="buttonContainer"  :onPress="()=>{ console.log('click') }">
            <text class="buttonText">
                {{ title }}
            </text>
        </touchable-opacity>
        
    </view>
</template>

<script>
export default {
    props:{
        title:{
            type: String,
            default:'titulo',
        },
        type:{
            type: String,
            default:'sm',
            validator: function(value){
                return ['sm','normal'].indexOf(value) !== -1
            }
        },
        background:{
            type: String,
            default:'success',
            validator: function(value){
                return ['normal','success','primary','danger'].indexOf(value) !== -1
            }
        }
    }
}
</script>

<style scoped>
.buttonContainer {
    padding-vertical: 10px;
    padding-horizontal: 15px;
    border-radius: 10px;
}

.normal{
    background-color: rgb(109, 4, 92);
}
.success{
    background-color: rgb(52, 121, 3);
}
.primary{
    background-color: rgb(5, 14, 141);
}
.danger{
    background-color: rgb(109, 4, 6);
}

.buttonText{
    color: #FFF;
    font-size: 18;
    font-weight: bold;
    align-self: center;
    text-transform: uppercase;
}


</style>