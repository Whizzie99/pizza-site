<template>
    <header>
        <div class="container clear">
            <div class="logo">
                <img :src="logoIcon" alt="">
            </div>
            <div class="nav">
                <img :src="menuIcon"
                    @click="showSidePanel = !showSidePanel"
                    alt="menu Icon"
                >
            </div>

            <md-drawer
            class="side-drawer"
                :md-right="true"
                :md-active.sync="showSidePanel"
            />

        </div>
    </header>
</template>


<script>
import logo from '../../assets/images/logo.png';
import menu from '../../assets/images/menu.png';


export default {
    data(){
        return{
            logoIcon: logo,
            menuIcon: menu,
            showSidePanel: false
        }
    }
}
</script>