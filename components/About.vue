<template>
    
    <section class="about-section mt-5" id="about">
		<div class="container">
			<div class="row">
				<div class="col-lg-6 offset-lg-3">
					<div class="main-title text-center">
						<h2 class="mt0">Nuestra misión es contigo</h2>
					</div>
				</div>
			</div>
			<div class="row mt-3">
				<div class="col-lg-8 col-xl-7">
					<div class="about_content">
						<p class="large">Somos una empresa joven con muchas ganas de crecer al lado de nuestros clientes con el fin de brindar la mayor variedad en materiales para la construcción y de ferreteria en general, bajo altos estandares de calidad y servicio acorde a las exigencias del mercado.</p> 
						
						<p class="large">Nos esforzamos día a día en ofrecer una alta gama de productos a fin de satisfacer las necesidades de nuestros clientes, con la finalidad de generar un crecimiento rentable, en beneficio de todos que nos permita mantener y mejorar cada día la calidad y servicio prestado.</p>

						<p> <span class="font-weight-bold">Teléfono: </span> (+58) 412-1081638</p>
						<p class="normal-text"> <span class="font-weight-bold">Dirección: </span> Calle Bolívar, Tacuato, Falcón, Venezuela</p>

						<ul class="ab_counting">
							<li class="list-inline-item">
								<div class="about_counting">
									<div class="icon"><span class="flaticon-user"></span></div>
									<div class="details">
										<h3>30</h3>
										<p>Clientes satisfechos</p>
									</div>
								</div>
							</li>
							<li class="list-inline-item">
								<div class="about_counting">
									<div class="icon"><span class="flaticon-box"></span></div>
									<div class="details">
										<h3>{{ productAmount }}</h3>
										<p>Productos</p>
									</div>
								</div>
							</li>
							<li class="list-inline-item">
								<div class="about_counting">
									<div class="icon"><span class="flaticon-high-five"></span></div>
									<div class="details">
										<h3>5</h3>
										<p>Aliados comerciales</p>
									</div>
								</div>
							</li>
						</ul>
					</div>
				</div>
				<div class="col-lg-4 col-xl-5">
					<div class="about_thumb">
						<img class="img-fluid w100" src="images/home1.jpg" alt="1.jpg">
					</div>
				</div>
			</div>

		</div>
	</section>

</template>

<script>
export default {
    name:"About",
	props:["productAmount"]
}
</script>

<style>
	.normal-text{
		margin-top: -20px;
	}
</style>