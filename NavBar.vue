<template>
    <!-- Login/Register component in every route -->
    <Login />
    <Register />
    <!-- Navbar/Routing -->
    <div class='bg-gray-900 text-gray-100 py-4 px-6 shadow-lg shadow-gray-950 md:flex justify-between items-center'> 
        <div class='flex items-center'>
            <span class='text-white text-x1 mr-1 flex items-center'>
                <a href='#/'> <i class="bi bi-cloud-lightning-rain text-2xl mr-1 text-indigo-500" ></i> </a>
                <a href='#/' class="ml-1"> <h1>FileOne</h1> </a>
            </span>
        </div>
        <ul class='md:flex md:items-center'>
            <li class="md:mx-4" v-for='element in Objects'>
                <a :href="element.link" class='text-white hover:text-indigo-500 focus:text-indigo-500 duration-200 text-sm' >{{element.name}}</a>
                
            </li>
            <div class= 'md:flex md:items-center border-gray-800 md:border-l-2 md:pl-3 md:mx-3'>
                <button type='button' id="login" class='mr-4 ml-4 hover:text-indigo-500 duration-200 focus:text-indigo-500 text-sm'> Login </button>
                <a href='#/pricing'> <Button class='ml-3 text-sm font-semibold'/></a>
            </div>
        </ul>
    </div>
    <component :is="currentView" />
</template>

<script>

    import Button from './NavBar-Button.vue'
    import Products from '../routes/Products.vue'
    import Pricing from '../routes/Pricing.vue'
    import Tutorial from '../routes/Tutorial.vue'
    import Home from '../routes/Home.vue'
    import NotFound from '../routes/NotFound.vue'
    import Login from '../components/Login.vue'
    import Register from '../components/Register.vue'

    const routes = {

    '/': Home,
    '/pricing': Pricing,
    '/products': Products,
    '/tutorial': Tutorial,
    '/*' : NotFound,

    }

    export default {

        data() {
            return { currentPath: window.location.hash }
        },

        computed: {
            currentView() {
                return routes[this.currentPath.slice(1) || '/'] || NotFound
                }
        },
        mounted() {
            window.addEventListener('hashchange', () => {
                this.currentPath = window.location.hash
		    })
        },
        components: {
            Button,
            Login,
            Register
        },
        
        setup() {
            
            let Objects = [
                {name : "Products" , link : "#/products" },
                {name : "Pricing" , link : "#/pricing" },
                {name : "Tutorial" , link : "#/tutorial" },
            ]
            return {Objects}
        }
    }
</script>
