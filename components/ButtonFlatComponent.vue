<template>
    <view :style="{ marginTop:15, marginLeft:'auto', marginRight: 'auto', width:'90%' }">
        <touchable-opacity class="buttonContainer" :onPress="()=>{ console.log('click') }">
            <text class="buttonText">
                Flat
            </text>
        </touchable-opacity>
        
    </view>
</template>

<style scoped>
.buttonContainer {
    padding-vertical: 10px;
    padding-horizontal: 15px;
    border-radius: 10px;
}

.buttonText{
    color: rgb(109, 4, 92);
    font-size: 18;
    font-weight: bold;
    align-self: center;
    text-transform: uppercase;
}


</style>