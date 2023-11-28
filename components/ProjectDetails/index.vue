<script setup>
    import projectListData from '~/assets/json/projectList.json'
    import { library } from '@fortawesome/fontawesome-svg-core'
    import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'
    import { faCode, faLink } from '@fortawesome/free-solid-svg-icons'
    library.add(faCode, faLink)

    const data = ref("")
    const title = ref("")
    const imgSrc = ref("")
    const tag = ref([])
    const intro = ref("")
    const codeSrc = ref("")
    const link = ref("")
    const route = useRoute()

    data.value = projectListData.project

    const itemDetailsData = data.value

    const setDetailsContent = (projectId)=> {
        for (let i = 0; i < itemDetailsData.length; i++) {
            if (itemDetailsData[i].itemNumber == projectId) {
                title.value = itemDetailsData[i].title
                imgSrc.value = itemDetailsData[i].imgSrc
                tag.value = itemDetailsData[i].tag
                intro.value = itemDetailsData[i].intro
                codeSrc.value = itemDetailsData[i].codeSrc
                link.value = itemDetailsData[i].link
            }
        }
    }

    onMounted(()=> {

        watchEffect(() => {
            const projectId = route.query.projectId
            if(projectId) {
                setDetailsContent(projectId)
            }
           
        })

    })

</script>

<template>
    <div class="case section">
        <div class="container">
            <div class="content_main_outside_box">
                <div class="content_main_box">
                    <div class="intro_box section_border">
                        <div class="image_box">
                            <img class="image" :src="imgSrc" width="750" height="480"
                                alt="">
                        </div>
                        <div class="text_box">
                            <div class="head_title_box">
                                <h1 class="title">{{ title }}</h1>
                            </div>
                            <div class="tag_box" >
                                <div class="tag" v-for="tagItem of tag">{{ tagItem }}</div>
                            </div>
                            <p class="text">{{ intro }}</p>
                            <ul class="link_box">
                                <li class="list">
                                    <p class="title">
                                        <font-awesome-icon icon="fa-solid fa-code" />
                                    </p>
                                    <a class="link" :href="codeSrc" target="_blank">{{ codeSrc }}</a>
                                </li>
                                <li class="list">
                                    <p class="title">
                                        <font-awesome-icon icon="fa-solid fa-link" />
                                    </p>
                                    <a class="link" :href="link" target="_blank">{{ link }}</a>
                                </li>
                            </ul>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<style lang="scss" scoped>
    .case {
        .head_title_box{
            margin: 0 auto;
            padding: 30px 0 10px;
            @include max-screen(767px){
                padding-top: 0;
            }
            .title{
                font-size: 36px;
                @include max-screen(991px){
                    font-size: 32px;
                }
            }
        }
        .content_main_outside_box{
            position: relative;

            .content_main_box{
                margin: 0 auto;
                .intro_box{
                    display: flex;
                    @include max-screen(767px){
                        flex-direction: column;
                    }
                    .image_box{
                        width: 40%;
                        padding-bottom: 30px;
                        @include max-screen(767px){
                            width: 100%;
                        }
                        .image{
                            width: 100%;
                            border-radius: var(--border-radius);
                        }
                    }
                    .text_box {
                        width: 60%;
                        padding: 0 30px 30px;
                        @include max-screen(767px){
                            width: 100%;
                        }
                        .tag_box {
                            display: flex;
                            align-items: center;
                            padding-bottom: 30px;
                            .tag {
                                font-size: 12px;
                                color: var(--font-color);
                                padding: 5px 10px;
                                margin-right: 10px;
                                background: var(--main);
                                border-radius: var(--border-radius);
                            }
                        }
                        .text {
                            margin-left: 5px;
                        }
                        .link_box {
                            padding-top: 10px;
                            margin-left: 5px;
                            .list {
                                display: flex;
                                .title {
                                    margin-right: 10px;
                                }
                                .link {
                                    color: var(--font-color);
                                }
                            }
                        }
                    }
                }
            }
        }
   }
</style>