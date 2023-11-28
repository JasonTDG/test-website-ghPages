<script setup>
    import mobileNav from "./mobileNav.vue"

    const isShow = ref(false)
    const isScroll = ref(false)
    const isAddNavBg = ref(false)

    const mobileNavToggle = () => {
        isShow.value = !isShow.value
    }

    const checkScrollEvent = ()=> {
        window.addEventListener("scroll", ()=> {
            if (window.pageYOffset > 0) {
                isAddNavBg.value = true
            } else {
                isAddNavBg.value = false
            }
        })
    }

    onMounted(()=> {
        checkScrollEvent()
    })

</script>

<template>
    <header :class="{ 'scrollnav' : isAddNavBg }">
        <div class="nav">
            <div class="container">
                <NuxtLink class="logo_box" href="/" title="Janyu" target="_self">
                    <img class="image" src="/logo.svg" alt="Janyu" width="104" height="54">
                </NuxtLink>    
                <div class="nav_box">
                    <ul class="nav_list">
                        <li class="list">
                            <NuxtLink class="link" to="/" title="作品案例" target="_self">作品案例</NuxtLink>
                        </li>
                        <li class="list">
                            <NuxtLink class="link" to="/about" title="關於我" target="_self">關於我</NuxtLink>
                        </li>
                        <li class="list">
                            <a class="link" href="#contact" title="與我聯繫" target="_self">與我聯繫</a>
                        </li>
                    </ul>
                    <div class="burger" @click="mobileNavToggle">
                        <div class="item"></div>
                        <div class="item"></div>
                        <div class="item"></div>
                    </div>
                </div>
            </div>
        </div>
        <mobileNav :isShow = "isShow" @updateState = "isShow = $event"/>
    </header>
</template>

<style lang="scss" scoped>
    header{
        position: fixed;
        width: 100%;
        top: 0;
        height: 90px;
        z-index: 100;
        &.scrollnav{
            background: var(--main-light);
        }
        .nav{
            width: 100%;
            height: 90px;
            position: fixed;
            
            &.hidden{
                &:before{
                    content: '';
                    position: absolute;
                    width: 100%;
                    height: 100%;
                    background: rgba(0, 0, 0, .7);
                }
            }
            .container{
                display: flex;
                justify-content: space-between;
                align-items: center;
                height: 100%;
            }
            .logo_box{
                height: 54px;
                transition: var(--transition);
                .image{
                    height: 100%;
                    filter: var(--logo);

                }
            }
            .nav_box{
                display: flex;
                align-items: center;
                .nav_list{
                    display: flex;
                    @include max-screen(767px){
                        display: none;
                    }
                    .list{
                        margin-left: 30px;
                        .link{
                            position: relative;
                            color: var(--body-normal);    
                        }
                        &:hover{
                            .link{
                                transition: var(--transition);
                                color: var(--nav-link-hover);
                            }
                        }
                    }
                }
                .mode_switch{
                    display: flex;
                    align-items: center;
                    margin-left: 30px;
                    .mode_btn{
                        padding: 0;
                        border: none;
                        background: transparent;
                        outline: none;
                        cursor: pointer;
                    }
                }
                .resume_btn{
                    margin-left: 30px;
                    @include max-screen(767px){
                        display: none;
                    }
                }
                .burger{
                    display: none;
                    margin-left: 15px;
                    cursor: pointer;
                    @include max-screen(767px){
                        display: block;
                    }
                    .item{
                        height: 2px;
                        background-color: var(--burger);
                        margin: 6px;
                        border-radius: var(--border-radius);
                        &:nth-child(1){
                            width: 20px;
                            margin-left: auto;
                        }
                        &:nth-child(2){
                            width: 18px;
                            margin-left: auto;
                        }
                        &:nth-child(3){
                            width: 24px;
                        }
                    }
                    
                }
            }
            }

        .mobile_nav{
            opacity: 0;
            visibility: hidden;
            position: fixed;
            top: 0;
            left: 0;
            display: flex;
            flex-direction: column;
            align-items: center;
            width: 100vw;
            height: 100vh;
            background: var(--body-bg);
            visibility: hidden;
            z-index: -1;
            &.show{
                opacity: 1;
                visibility: visible;
                z-index: 99;
                &::before{
                    content: '';
                    position: absolute;
                    top: 0;
                    left: 0;
                    width: 100%;
                    height: 100%;
                    background: var(--mobile-nav-bg);
                }
            }
            .burger_opened{
                position: absolute;
                top: 0;
                right: 0;
                width: 75px;
                height: 75px;
                padding: 20px 20px 35px 35px;
                border-radius: 0 0 0 100%;
                background: var(--highlight);
                z-index: 99;
                cursor: pointer;
                .item{
                    width: 24px;
                    height: 2px;
                    background-color: var(--burger);
                    margin: 6px;
                    border-radius: var(--border-radius);
                    &:nth-child(1){
                        transform: rotate(-45deg) translate(-7px,-4px);
                    }
                    &:nth-child(2){
                        transform: rotate(45deg) translate(-10px,2px);
                    }
                }
            }
            .inner_box{
                padding: 100px 5% 5%;
                &.container{
                    display: block;
                }
                .logo_box{
                    display: block;
                    margin-bottom: 60px;
                    .image{
                        width: 140px;
                        height: auto;
                        filter: var(--logo);
        
                    }
                }
                .mobile_nav_list{   
                    padding: 15px 5px;
                    margin-bottom: 30px;
                    border-bottom: 1px solid var(--item-gray);
                    .mobile_list{
                        padding: 15px 0;
                        .link{
                            position: relative;
                            color: var(--body-normal);
                            font-size: 18px;
                            &:after{
                                content: '';
                                position: absolute;
                                left: 0;
                                bottom: -10px;
                                width: 100%;
                                height: 2px;
                                background: var(--main-color);
                                opacity: 0;
                            }
                        }
                    }
                }
                .social_media{
                display: flex;
                align-items: center;
                padding: 0 5px; 
                .link {
                    display: block;
                    align-items: center;
                    margin-right: 25px;

                    &:last-child {
                        margin-right: 0;
                    }

                    &:hover {
                        opacity: .6;
                    }

                    .image {
                        width: auto;
                        height: 24px;
                        filter: var(--social-media);
                    }
                }
                }
                .resume_btn{
                    width: 100%;
                    margin-top: 45px;
                    text-align: center;
                }
            }

        }
    }
</style>