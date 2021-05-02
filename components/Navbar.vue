<template>
    <nav class="navbar navbar-expand-md fixed-top navbar-light bg-light ">
		<a class="nav-link" href="#">
			<img class="logo" src="images/logo.png">
		</a>
				
		<div class="navbar-collapse collapse w-100 order-3 dual-collapse2">
			<ul class="navbar-nav ml-auto">
				<li class="nav-item">
					<a :class="activeLink == 'home' ? mainClass+' active' : mainClass " @click="goTo('home')">Inicio</a>
				</li>
				<li class="nav-item">
					<a :class="activeLink == 'about' ? mainClass+' active' : mainClass" @click="goTo('about')">Nosotros</a>
				</li>
				<li class="nav-item">
					<a :class="activeLink == 'product' ? mainClass+' active' : mainClass" @click="goTo('product')">Productos</a>
				</li>
			</ul>
		</div>

		<div class=" order-3 d-none d-sm-block d-md-none d-block">
			<ul class="navbar-nav ml-auto">
				<li class="nav-item">
					<button class="btn btn-light" data-toggle="modal" data-target=".navModal"><i class="fa fa-bars"></i></button>
				</li>
			</ul>
		</div>


		<div class="modal fade navModal" id="navModal" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
			<div class="modal-dialog modal-lg modal-dialog-centered">
				<div class="modal-content">
				<div class="modal-header">
					<button type="button" class="close" data-dismiss="modal" aria-label="Close">
					<span aria-hidden="true">&times;</span>
					</button>
				</div>
				<div class="modal-body">
					<div class="container">
						<div class="row">
							<div class="col-md-12">

								<h3 data-dismiss="modal" :class="activeLink == 'home' ? navbarMainClass+' active' : navbarMainClass" @click="goTo('home')">Inicio</h3>
								<h3 data-dismiss="modal" :class="activeLink == 'about' ? navbarMainClass+' active' : navbarMainClass" @click="goTo('about')">Nosotros</h3>
								<h3 data-dismiss="modal" :class="activeLink == 'product' ? navbarMainClass+' active' : navbarMainClass" @click="goTo('product')">Productos</h3>

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

	</nav>
</template>

<script>
    export default {
        name:"Navbar",
		data(){
			return{
				mainClass:"nav-link cursor-pointer font-weight-bold ml-2 mr-2", 
				navbarMainClass:"text-center cursor-pointer",
				activeLink:"home"
			}
		},
		methods:{
			goTo(identifier){

				const element = document.getElementById(identifier)
				let distance = element.offsetTop

				window.scrollTo({
					top: distance,
					left: 0,
					behavior: 'smooth'
				});

				this.setActiveLink(identifier)
				


			},
			setActiveLink(link){

				this.activeLink = link

			},
			isActiveLink(link){
				return this.activeLink == link ? 'active' : ''
			}
		}
    }
</script>

<style>

	nav{
		padding-top: 1rem !important;
		padding-bottom: 1rem !important;
	}

	.active{
		color: rgb(255, 90, 95) !important;
	}

	.bg-light{
		background-color: #fff !important;
	}

	.btn-light{
		background-color: #fff !important;
	}

	.logo{
		width: 100px;
	}

	.modal-backdrop{
		z-index: 0 !important;
	}

</style>