<script setup>
    import { register } from 'swiper/element/bundle'
    import '../../../node_modules/swiper/swiper-bundle.min.css'

    const setSwiper = ()=> {
        register()
    }

    onMounted(()=> {
        setSwiper()
    })
</script>

<template>
    <div class="banner section">
        <div class="container">
            <div class="text_box">
                <div class="title_box">
                    <h1 class="title">我是 Janyu 👋🏻</h1>
                </div>
                <div class="intro_box">
                    <p class="intro_text">
                        擁有4年的網頁設計經驗，<br>
                        從同時學習設計和程式，到決心專注前端開發。
                    </p>
                </div>
            </div>
            <div class="image_box">
                <img class="image" src="/banner_img.png"  width="480" height="372" alt="Janyu">
            </div>
        </div>
    </div>
</template>

<style lang="scss" scoped>
    .banner {
        .container {
            position: relative;
            display: flex;
            justify-content: space-between;
            align-items: center;

            @include max-screen(767px) {
                flex-direction: column-reverse;
            }

            .text_box {
                margin-right: 30px;
                @include max-screen(767px) {
                    margin-right: 0;
                }

                .title_box {
                    padding-bottom: 15px;
                    .title{
                        @include max-screen(767px) {
                            text-align: center;
                        }
                    } 
                }
                .intro_box{
                    font-weight: 500;
                    .intro_text{
                        color: var(--font-color);
                        font-size: 24px;
                        @include max-screen(991px) {
                            font-size: 20px;
                        }
                    }
                    .slogan_box {
                        display: flex;
                        align-items: center;
                        .text {
                            color: var(--font-color);
                            font-size: 24px;
                            @include max-screen(991px) {
                                font-size: 20px;
                            }
                        }

                        .carousel_box {
                            width: fit-content;
                            height: 40px;
                            margin: 0 5px;
                            padding: 0 12px;
                            font-size: 16px;
                            font-weight: 500;
                            @include max-screen(991px) {
                                height: 36px;
                            }
                            &::before {
                                content: '';
                                position: absolute;
                                bottom: 0;
                                left: 0;
                                width: 100%;
                                height: 25px;
                                border-radius: var(--border-radius);
                                background-color: var(--highlight);
                                
                            }

                            .carousel_text{
                                font-size: 24px;
                                @include max-screen(991px) {
                                    font-size: 20px;
                                }
                            }                            
                        }
                    }

                }
            }

            .image_box {
                position: relative;
                width: 40%;
                overflow: hidden;
                @include max-screen(767px) {
                    width: 100%;
                    max-width: 400px;
                    margin: 0 auto 60px;
                }
                &::before{
                    content: '';
                    position: absolute;
                    left: 50%;
                    bottom: -26%;
                    width: 73%;
                    padding-bottom: 73%;
                    border-radius: 100%;
                    background: var(--banner-img-bg);
                    transform: translateX(-50%);
                }

                .image {
                    position: relative;
                    width: 100%;
                }
            }
        }

        .mobile_title_box {
            display: none;
            position: absolute;
            bottom: 40px;
            width: 100%;
            background: var(--body-other);
            border: 1px solid rgba(var(--main-color), 0.6);

            @include max-screen(480px) {
                display: block;
                border-left: none;
                border-right: none;
            }

            .title {
                font-size: 32px;
                font-weight: normal;
                text-align: center;
                color: var(--main-color);
                padding: 10px;
            }
        }
    }
</style>