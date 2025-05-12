<template>
    <div class="container">
        
        <div class="row py-5">
            <HeaderComponent/>
        </div>

        <div class="row py-5">

            <div class="col-4">
                <LinksComponent/>
            </div>
            <div class="col-8">
              <BodyComponent/>
            </div>

        </div>


        <div class="row py-5">
            <FooterComponent/>
        </div>

    </div>
</template>

<script>
    import HeaderComponent from './components/Header/HeaderComponent.vue'
    import FooterComponent from './components/Footer/FooterComponent.vue'
    import LinksComponent from './components/Links/LinksComponent.vue'
    import BodyComponent from './components/DataTable/BodyComponent.vue'

    export default{
        components:{
            HeaderComponent,
            FooterComponent,
            LinksComponent,
            BodyComponent
        }
    }
</script>