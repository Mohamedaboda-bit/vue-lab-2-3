<template>
    <div class="app-container d-flex flex-column min-vh-100 w-100">
        
        <div class="row py-5">
            <HeaderComponent/>
        </div>
        <div class="col-8">
              <BodyComponent />
        </div>
        <div class="row py-5">
            <FooterComponent/>
        </div>

    </div>
</template>

<script>
    import HeaderComponent from './components/Header/HeaderComponent.vue'
    import BodyComponent from './components/DataTable/BodyComponent.vue'
    import FooterComponent from './components/Footer/FooterComponent.vue'    


    export default{
        components:{
            HeaderComponent,
            BodyComponent,
            FooterComponent
            
        }
    }
</script>