<template>
    
    <div id="home">
        <div class="cover">
            <div class="container">
                <div class="row">
                    
                    <div class="col-12 box">
                        <h1 class="text-center text-white">FERREMUNDO</h1>
                        <h4 class="text-center text-white">Somos tu mejor opción en el mundo de la ferretería</h4>
                    </div>

                </div>
            </div>
        </div>
        <div class="hero"></div>
    </div>

</template>

<script>
    export default {
        name:"Header"
    }
</script>

<style>

    .hero{
        background-image: url('/images/landing.jpg');
        background-size: cover;
        min-height: 100vh;
    }

    .cover{
        width: 100%;
        z-index: 10;
        position: absolute;
        background-color: rgba(255, 90, 95, 0.3);
        min-height: 100vh;
    }

    .box {
        display: flex;           /* establish flex container */
        flex-direction: column;  /* make main axis vertical */
        justify-content: center; /* center items vertically, in this case */
        align-items: center;     /* center items horizontally, in this case */
        height: 100vh;
    }

    h1{
        font-size: 4rem;
    }

</style>