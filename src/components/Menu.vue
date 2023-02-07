<template>
    <div class="menu">
        <div class="sidebar-toggle">
            <b-button v-b-toggle.sidebar-no-header>
                <img src="../assets/images/svg/menu.svg">
            </b-button>
        </div>
    </div>
</template>

<style scoped>
    .menu{
        padding: 10px 20px;
        background-color: #17a2b8;
        z-index: 10005;
        position: relative;
    }
    .sidebar-toggle > button{
        background-color: transparent;
        border: 0;
        outline: none;
    }
    .sidebar-toggle > button:active{
        background-color: transparent;
        border: 0;
        outline: none
    }
    .sidebar-toggle > button > img{
        width: 20px;
    }
</style>