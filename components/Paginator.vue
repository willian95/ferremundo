<template>
    <div class="col-lg-12 mt20">
        <div class="mbp_pagination">
            <ul class="page_navigation">
                <li class="page-item">
                    <a class="page-link cursor-pointer" @click="changePage(page - 1)"  v-show="page > 1"> <span class="flaticon-left-arrow"></span> Prev</a>
                </li>
                <li :class=" page == index ? 'page-item active' : 'page-item'" v-for="index of pages" v-bind:key="index" @click="changePage(index)">
                    <a class="page-link cursor-pointer">{{ index }}</a>
                </li>
                <li class="page-item">
                    <a class="page-link cursor-pointer" @click="changePage(page + 1)" v-show="page < pages" ><span class="flaticon-right-arrow"></span></a>
                </li>
            </ul>
        </div>
    </div>
</template>

<script>
export default {
    name:"Paginator",
    props:{
        'amountToShow':Number,
        'total':Number,
        'model':Array,
        'setPage':{type: Function}
    },
    data(){
        return{
            pages:1,
            page:1
        }
    },
    methods:{

        changePage(index){
            this.page = index
            this.setPage(index)
        },

    },
    watch: { 
        total: function(newVal, oldVal) { // watch it
            this.pages = Math.ceil(this.total / this.amountToShow)
        }
    },
    created(){
        this.pages = Math.ceil(this.total / this.amountToShow)
    }

}
</script>