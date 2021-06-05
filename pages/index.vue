<template>
  
  <div>
    
    <Header />
    <About :productAmount="mainProducts.length"/>

    <div class="container" id="product">
      <div class="row">
        <div class="col-12 main-title mb-5">
            <h2 class="mt0 text-center">Nuestros productos</h2>
        </div>
      </div>
      <div class="row">
        <div class="col-md-4 mb-5">
          <div class="form-group">
            <input type="text" class="form-control" placeholder="Búsqueda" @keyup="search()" v-model="query">
          </div>
        </div>
      </div>
      <div class="row">
        <div class="col-lg-4 col-md-6 col-sm-12" v-for="(product, index) in productsToShow" v-bind:key="index">
          <ProductCard :product="product" :setSelectedProduct="setSelectedProduct"/>
        </div>
        <Paginator :amountToShow="amountToShow" :total="products.length" :model="productsToShow" :setPage="setPage" />
      </div>

    </div>

    <ProductModal :product="selectedProduct" />

  </div>

</template>

<script>

  import Header from '../components/Header'
  import About from '../components/About'
  import ProductCard from '../components/ProductCard'
  import ProductModal from '../components/ProductModal'
  import Paginator from '../components/Paginator'

  export default {
    
    components: { About, ProductCard, Header, ProductModal, Paginator},
    data(){
      return{
        query:"",
        products:[],
        productsToShow:[],
        page:1,
        amountToShow:12,
        selectedProduct:null,
        mainProducts:[
          {
            title:"Resistencias de cocina",
            category:"Hogar",
            price: "5",
            image:"products/minified/resistencia-cocina-min.jpg"
          },
          {
            title:"Alicate de presión",
            category:"Hogar",
            price: "8",
            image:"products/minified/alicate-1-min.jpg"
          },
          {
            title:"Pega tanke",
            category:"Hogar",
            price: "2.5",
            image:"products/minified/pegatamke-min.jpg"
          },
          {
            title:"Tape",
            category:"Hogar, Construcción",
            price: "0.8",
            image:"products/minified/teipe-1-min.jpg"
          },
          {
            title:"Lija 120",
            category:"Construcción",
            price: "1",
            image:"products/minified/lija-p120-min.jpg"
          },
          {
            title:"Lija 80",
            category:"Construcción",
            price: "1",
            image:"products/minified/lija-p80-min.jpg"
          },
          {
            title:"Lija 600",
            category:"Construcción",
            price: "1",
            image:"products/minified/lija-3w-min.jpg"
          },
          {
            title:"Teflón",
            category:"Hogar, Construcción",
            price: "1.5",
            image:"products/minified/cinta-de-sellado-1-min.jpg"
          },
          {
            title:"Extensión electrica",
            category:"Hogar",
            price: "3.5",
            image:"products/minified/extension-min.jpg"
          },
          {
            title:"Brocha 1 pulgada",
            category:"Hogar",
            price: "3",
            image:"products/minified/brocha-cebra-azul-min.jpg"
          },
          {
            title:"Brocha 2 pulgadas",
            category:"Hogar",
            price: "3",
            image:"products/minified/brocha-prestigio-50.8-min.jpg"
          },
          {
            title:"Brocha 3 pulgadas",
            category:"Hogar",
            price: "3.5",
            image:"products/minified/brocha-prestigio-76.2-min.jpg"
          },
          {
            title:"Brocha 3.5 pulgadas",
            category:"Hogar",
            price: "3.5",
            image:"products/minified/brochas-pitbull-min.jpg"
          },
          {
            title:"Adaptador de 3 a 2 patas",
            category:"Hogar",
            price: "1.5",
            image:"products/minified/enchufe-naranja-2-min.jpg"
          },
          {
            title:"Toma de corriente sencilla",
            category:"Hogar",
            price: "1",
            image:"products/minified/enchufe-2-puntas-min.jpg"
          },
          {
            title:"Toma de corriente doble",
            category:"Hogar",
            price: "2.5",
            image:"products/minified/enchufe-3-puntas-min.jpg"
          },
          {
            title:"Socate",
            category:"Hogar",
            price: "1",
            image:"products/minified/socates-min.jpg"
          },
          {
            title:"Apagadores",
            category:"Hogar",
            price: "1",
            image:"products/minified/interruptor-min.jpg"
          },
          {
            title:"Silicon gris",
            category:"Hogar",
            price: "2.5",
            image:"products/minified/pega-gris-min.jpg"
          },
          {
            title:"Bombillos 12W",
            category:"Hogar",
            price:"1.5",
            image:"products/minified/hug-led-A75-min.jpg"
          },
          {
            title:"Electrodos",
            category:"Soldadura",
            price: "0.1",
            image:"products/minified/electrodos-min.jpg"
          },
          {
            title:"Conectores rj45 blindados",
            category:"Hogar, Redes",
            price: "0.1",
            image:"products/minified/conectores-RJ45-min.jpg"
          },
          {
            title:"Junta 1/2",
            category:"Hogar, Plomería",
            price: "2",
            image:"products/minified/tubo-blanco-1-min.jpg"
          },
          {
            title:"Junta 3/4",
            category:"Hogar, Plomería",
            price: "3",
            image:"products/minified/tubo-blanco-3-min.jpg"
          },
          {
            title:"Pega PVC",
            category:"Hogar, Plomería",
            price: "4",
            image:"products/minified/pega-min.jpg"
          },
          {
            title:"Codos 1/2",
            category:"Hogar, Plomería",
            price: "0.8",
            image:"products/minified/codos-min.jpg"
          },
          {
            title:"Codos 3/4",
            category:"Hogar, Plomería",
            price: "1",
            image:"products/minified/codos-min.jpg"
          },
          {
            title:"Tee 1/2",
            category:"Hogar, Plomería",
            price: "0.8",
            image:"products/minified/tubos-T-min.jpg"
          },
          {
            title:"Tee 3/4",
            category:"Hogar, Plomería",
            price: "1",
            image:"products/minified/tubos-T-min.jpg"
          },
          
          {
            title:"Anzuelos de pesca",
            category:"Pesca",
            price:"1",
            extra:"x 5",
            image:"products/minified/anzuelos-min.jpg"
          },
          {
            title:"Luces de pesca",
            category:"Pesca",
            price:"5",
            image:"products/minified/tajali-min.jpg"
          },
          {
            title:"Cuchilla de licuadora",
            category:"Hogar",
            price:"5",
            image:"products/minified/cuchilla-min.jpg"
          },
          {
            title:"Hojas de segueta 24 dientes",
            category:"Ferretería",
            price:"1.5",
            image:"products/minified/lenox-min.jpg"
          },
          {
            title:"Cuadrantes de licuadora",
            category:"Hogar",
            price:"1",
            image:"products/minified/cuadrante-min.jpg"
          },
          
        ]
      }
    },
    methods:{
      fetchProducts(){

        this.sortMainProductsOrder()

        this.products = this.mainProducts

        var skip = (this.page - 1) * this.amountToShow;
        var taken = 0;
        var index = 0;

        this.productsToShow = this.products.filter(data => {

          if(index >= skip){

              if(taken < this.amountToShow ){
                taken ++
                return data 
              }
            
          }  

          index++

        })

        this.sortOrder()
      },
      search(){

        this.sortMainProductsOrder()

        var skip = (this.page - 1) * this.amountToShow;
        var taken = 0;
        var index = 0;

        this.products = this.mainProducts.filter(data => {

          if(data.title.toLowerCase().indexOf(this.query.toLowerCase()) >= 0)
          {    
              return data 
          } 

        })

        this.productsToShow = this.mainProducts.filter(data => {

          if(index >= skip){

            if(data.title.toLowerCase().indexOf(this.query.toLowerCase()) >= 0)
            {
              if(taken < this.amountToShow){
                taken ++
                return data 
              }
              
            } 

          }  

          index++

        })

        this.sortOrder()

      },
      setSelectedProduct(product){
        this.selectedProduct = product
      },
      sortMainProductsOrder(){

        this.mainProducts.sort(function(a, b){
          if(a.title < b.title) { return -1; }
          if(a.title > b.title) { return 1; }
          return 0;
        })

      },
      sortOrder(){
        
        this.productsToShow.sort(function(a, b){
          if(a.title < b.title) { return -1; }
          if(a.title > b.title) { return 1; }
          return 0;
        })
      },
      setPage(page){

        this.page = page
        if(this.query == ""){
          this.fetchProducts()
        }else{
          this.search()
        }

      }

    },
    created(){

      this.fetchProducts()

    }

  }
</script>
