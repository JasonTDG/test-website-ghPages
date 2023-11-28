<script setup>
    const title = ref("作品案例")
    const enTitle = ref("Project")
</script>

<template>
    <div class="design_case">
        <div class="container">
            <SectionTitle :title="title" :enTitle="enTitle"/>
            <div class="case_box">
                <ProjectList />
            </div>
        </div>
    </div>
</template>

<style lang="scss" scoped>
    .design_case {
        position: relative;
        padding: 30px 0 90px;
        overflow: hidden;
        &::before{
            content: '';
            position: absolute;
            width: 50%;
            padding-bottom: 50%;
            top: 0;
            left: 0;
            border-radius: 100%;
            background: var(--background-cirle);
            transform: translateX(-52%);
        }
        &::after{
            content: '';
            position: absolute;
            width: 32%;
            padding-bottom: 32%;
            right: 0;
            bottom: 0;
            border-radius: 100%;
            background: var(--background-cirle);
            transform: translate(20%, 40%);
        }
        .container {
                z-index: 1;
        }

        .case_box{
            display: flex;
            padding-top: 30px;
            flex-wrap: wrap;
            justify-content: space-between;
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
                    padding-bottom: 75%;
                    margin-bottom: 15px;
                    border-radius: var(--border-radius);
                    transition: var(--transition);
                } 
                .text_box {
                        padding-left: 5px;
                    .case_title {
                        color: var(--body-normal);
                        padding-bottom: 5px;
                    }

                    .intro {
                        font-size: 16px;
                        color: var(--font-color);
                    }
                }
                &:hover{
                    .image_box{
                        background-size: 105%;
                        
                    }
                }
            }
        }
    }
    
    
</style>


