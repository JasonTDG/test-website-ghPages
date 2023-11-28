<script setup>

    const title = ref("與我聯繫")
    const enTitle = ref("Contact")

</script>

<template>
   <div class="contact" id="contact">
        <div class="container">
            <div class="text_box">
                <SectionTitle :title="title" :enTitle="enTitle"/>
                <p class="text">無論是在設計或是生活，每一次的討論及分享總是讓我感到快樂，彼此給予的反饋也能夠創造出不一樣的思維。如果有任何問題及想法，歡迎與我聯繫 ！期待與你的每一次交流。 </p>
                <a class="btn" href="mailto:janyu427130@gmail.com" target="_blank">
                    與我聯繫
                </a>
            </div>
            <div class="image_box">
                <img class="image" src="/mail_img.svg" width="320" height="296" alt="與我聯繫">
            </div>
        </div>
    </div>
</template>

<style lang="scss">
    .contact {
       background-color: var(--main-light);
       padding: 60px 0;

       .container {
           display: flex;
           align-items: center;
           justify-content: space-between;

           @include max-screen(767px) {
               flex-direction: column-reverse;
               align-items: flex-start;
           }

           .text_box {
               width: 50%;
               margin-right: 30px;
               @include max-screen(768px) {
                   width: 100%;
                   margin-right: 0;
               }

               .text {
                   padding-bottom: 30px;
               }
           }

           .image_box {
               width: 40%;
               max-width: 320px;
               @include max-screen(767px) {
                   width: 100%;
                   margin-bottom: 30px;
                   max-width: 240px;
               }
               @include max-screen(480px) {
                    max-width: 160px;
                }

               .image {
                   width: 100%;
               }
           }
       }
   }
</style>

