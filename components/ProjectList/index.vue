
<script setup>
    import projectListData from '~/assets/json/projectList.json'

    const data = ref("")
    const projectId = ref("")

    data.value = projectListData.project
    
</script>

<template>
    <div class="item" v-for="item of data" :key="item.key">
        <NuxtLink class="link" :to="'/project?projectId=' + item.itemNumber">
            <div class="image_box">
                <img class="image" :src="item.imgSrc">
            </div>
            <div class="text_box">
                <h2 class="case_title">{{ item.title }}</h2>
                <div class="tag_box" >
                    <div class="tag" v-for="tagItem of item.tag">{{ tagItem }}</div>
                </div>
            </div>
        </NuxtLink>
    </div>
</template>

<style lang="scss" scoped>

    .item {
        width: calc(50% - 15px);
        margin-bottom: 50px;

        @include max-screen(768px) {
            margin-bottom: 30px;
        }

        @include max-screen(480px) {
            width: 100%;
        }
            
        .image_box {
            margin-bottom: 15px;
            .image {
                border-radius: var(--border-radius);
            }
        } 
        .text_box {
            padding-left: 5px;
            .case_title {
                color: var(--body-normal);
                padding-bottom: 10px;
            }

            .tag_box {
                display: flex;
                align-items: center;
                .tag {
                    font-size: 12px;
                    color: var(--font-color);
                    padding: 5px 10px;
                    margin-right: 10px;
                    background: var(--main);
                    border-radius: var(--border-radius);
                }
            }
        }
        &:hover{
            .image_box{
                background-size: 105%;
            }
        }
    }

</style>

