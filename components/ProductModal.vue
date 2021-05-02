<template>
    <div class="modal fade" id="productModal" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
        <div class="modal-dialog modal-lg modal-dialog-centered">
            <div class="modal-content">
            <div class="modal-header">
                <h3 class="modal-title" id="exampleModalLabel" v-if="product">{{ product.title }}</h3>
                <button type="button" class="close" data-dismiss="modal" aria-label="Close">
                <span aria-hidden="true">&times;</span>
                </button>
            </div>
            <div class="modal-body">
                <div class="container">
                    <div class="row">
                        <div class="col-md-5">
                            <img :src="'images/'+product.image" class="w-100" v-if="product">
                        </div>
                        <div class="col-md-7">

                            <h4 v-if="product"><span class="text-thm">Categoría:</span> {{ product.category }}</h4>
                            <h4 v-if="product"><span class="text-thm">Precio</span> $ {{ product.price }}</h4>

                        </div>

                    </div>

                </div>
            </div>
            <div class="modal-footer">
                <!--<button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
                <button type="button" class="btn btn-primary">Save changes</button>-->
            </div>
            </div>
        </div>
    </div>    
</template>

<script>
    export default {
        name:"ProductModal",
        props:["product"]
    }
</script>