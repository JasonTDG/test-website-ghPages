<script setup>
   import aboutData from '~/assets/json/about.json'

   const data = aboutData.about.intro
   const title = data.title
   const text = data.text

</script>

<template>
    <div class="main_section">
        <div class="container">
            <div class="text_box">
                <div class="title">{{ title }}</div>
                <p class="intro">
                    {{ text }}
                </p>
            </div>
            <div class="image_box">
                <img class="image" src="/janyu.jpg" alt="">
            </div>
        </div>
    </div>
</template>

<style lang="scss">
    .main_section {
        padding: 60px 0 30px;
        .container {
            display: flex;
            align-items: center;
            justify-content: space-between;
            @include max-screen(480px) {
                flex-direction: column-reverse;
            }
            .text_box {
                width: 50%;
                @include max-screen(480px) {
                    width: 100%;
                }
                .title {
                    font-size: 32px;
                    font-weight: 500;
                    margin-bottom: 30px;
                    color: var(--body-normal);

                    @include max-screen(768px) {
                        font-size: 28px;
                    }
                }
                .intro {
                    color: var(--font-color);
                }
            }
            .image_box{
                width: 45%;
                @include max-screen(480px) {
                    width: 100%;
                    padding-bottom: 30px;
                }
                .image{
                    width: 100%;
                    background: #ccc;
                    border-radius: 5px;
                }
            }
        }
    }
</style>

