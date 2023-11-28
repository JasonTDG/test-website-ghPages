<script setup>

    import { library } from '@fortawesome/fontawesome-svg-core'
    import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'
    import { faGithub, faLinkedin } from '@fortawesome/free-brands-svg-icons'
    import { faEnvelope } from '@fortawesome/free-solid-svg-icons'
    library.add(faGithub, faEnvelope, faLinkedin)

    const props = defineProps({
        isShow: {
            type: Boolean,
            default: false
        }
    })

    const emits = defineEmits({
        updateState: {
            type: Boolean,
            default: false
        }
    })

    const closeMobileNav = () => {
        emits('updateState', false);
    }

</script>

<template>
    <div class="mobile_nav" :class="{'show': isShow}" v-if="isShow">
        <div class="burger_opened" @click="closeMobileNav">
            <div class="item"></div>
            <div class="item"></div>
        </div>
        <div class="inner_box container">
            <NuxtLink class="logo_box" href="/" title="Janyu" target="_self">
                <img class="image" src="/logo.svg" alt="Janyu" width="104" height="54">
            </NuxtLink> 
            <ul class="mobile_nav_list">
                <li class="mobile_list">
                    <NuxtLink class="link" to="/" title="作品案例" target="_self" @click="closeMobileNav">作品案例</NuxtLink>
                </li>
                <li class="mobile_list">
                    <NuxtLink class="link" to="/about" title="關於我" target="_self" @click="closeMobileNav">關於我</NuxtLink>
                </li>
                <li class="mobile_list">
                    <a class="link" href="#contact" title="與我聯繫" target="_self" @click="closeMobileNav">與我聯繫</a>
                </li>
            </ul>
            <div class="social_media">
                <a class="link" target="_blank" href="https://www.instagram.com/jan__yu" title="Github">
                    <font-awesome-icon class="icon" icon="fa-brands fa-github" />
                </a>
                <a class="link" target="_blank" href="mailto:janyu427130@gmail.com" title="Email" alt="E-mail">
                    <font-awesome-icon class="icon" icon="fa-solid fa-envelope" />
                </a>
                <a class="link" target="_blank" href="https://www.linkedin.com/in/chen-yu-wu-design" title="Linkedin">
                    <font-awesome-icon class="icon" icon="fa-brands fa-linkedin" />
                </a>
            </div>
        </div>
    </div>
</template>

<style lang="scss" scoped>
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

                .icon {
                    width: auto;
                    height: 24px;
                    color: var(--font-color);
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
</style>