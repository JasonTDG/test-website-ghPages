<script setup>
    import contactSection from './contactSection.vue'
    import { library } from '@fortawesome/fontawesome-svg-core'
    import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'
    import { faGithub, faLinkedin } from '@fortawesome/free-brands-svg-icons'
    import { faEnvelope } from '@fortawesome/free-solid-svg-icons'
    library.add(faGithub, faEnvelope, faLinkedin)

    const isShowSideIcon = ref(false)

    const goTop = ()=> {
        window.scrollTo({
            top: 0,
            behavior: "smooth"
        })
    }

    const checkScrollEvent = ()=> {
        window.addEventListener("scroll", ()=> {
            if (window.pageYOffset > 400) {
                isShowSideIcon.value = true
            } else {
                isShowSideIcon.value = false
            }
        })
    }

    onMounted(()=> {
        checkScrollEvent()
    })

</script>

<template>
    <contactSection />
    <footer>
        <div class="container">
            <p class="copyright">© Janyu <span id="thisYear"></span> All Rights Reserved</p>
            <div class="social_media">
                <a class="link" target="_blank" href="https://github.com/Janyu427" title="Github">
                    <font-awesome-icon class="icon" icon="fa-brands fa-github" />
                </a>
                <a class="link" target="_blank" href="mailto:janyu427130@gmail.com" title="Email">
                    <font-awesome-icon class="icon" icon="fa-solid fa-envelope" />
                </a>
                <a class="link" target="_blank" href="https://www.linkedin.com/in/chen-yu-wu-design" title="Linkedin">
                    <font-awesome-icon class="icon" icon="fa-brands fa-linkedin" />
                </a>
            </div>
        </div>
    </footer>
    <div class="side_icon" v-if="isShowSideIcon">
        <span class="gotop" @click="goTop"></span>
    </div>
</template>

<style lang="scss">
    footer {
       padding: 30px 0;

       .container {
           display: flex;
           justify-content: space-between;

           .copyright {
               font-size: 12px;
           }

           .social_media {
               display: flex;
               align-items: center;

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
       }
   }
   
</style>

