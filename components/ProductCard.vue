<template>
    <div class="feat_property home7 style4" data-toggle="modal" data-target="#productModal" @click="setSelectedProduct(product)">
        <div class="thumb">
            <div class="fp_single_item_slider owl-carousel owl-theme owl-loaded">
            
                <img class="img-whp" :src="'images/'+product.image" alt="fp2.jpg">
            </div>
            <div class="thmb_cntnt style2">
                <ul class="tag mb0">
                    <li class="list-inline-item dn"></li>
                </ul>
            </div>
            <div class="thmb_cntnt style3">
                <a class="fp_price cursor-pointer">${{ product.price }}<small v-if="product.extra"> {{ product.extra }}</small></a>
            </div>
        </div>
        <div class="details">
            <div class="tc_content">
                <p class="text-thm">{{ product.category }}</p>
                <h4>{{ product.title }}</h4>
            </div>
        </div>
    </div>
</template>

<script>

    export default{
        
        name:"ProductCard",
        props:{
            'product':Object, 
            "setSelectedProduct":{ type: Function }
        }

    }
</script>

<style>

    .img-whp{
        margin-top: -80px;
    }

</style>