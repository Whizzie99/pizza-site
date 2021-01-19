<template>
    <footer>
        <div class="container">
            <div>
                <img :src="logoIcon" alt="Logo">
                <div class="contact">
                    <div>Call us</div>
                    <div>45677-7778</div>
                </div>
            </div>
        </div>
    </footer>
</template>


<script>
import logo from '../../assets/images/logo.png';


export default {
    data(){
        return{
            logoIcon: logo
        }
    }
}
</script>