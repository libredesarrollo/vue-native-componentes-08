<template>
    <view :style="{ marginTop:15, marginLeft:'auto', marginRight: 'auto', width:'90%' }">
        <touchable-opacity  :style="[ type == 'sm' ? { alignSelf:'center' } : {} ]" :class="[border]" class="buttonContainer"  :onPress="()=>{ console.log('click') }">
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
        border:{
            type: String,
            default:'danger',
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
    border-color: rgb(109, 4, 92);
    border-width:2px;
}
.success{
    border-color: rgb(52, 121, 3);
    border-width:2px;
}
.primary{
    border-color: rgb(5, 14, 141);
    border-width:2px;
}
.danger{
    border-color: rgb(109, 4, 6);
    border-width:2px;
}

.buttonText{
    color: #000;
    font-size: 18;
    font-weight: bold;
    align-self: center;
    text-transform: uppercase;
}


</style>