<script setup>
    import aboutData from '~/assets/json/about.json'

    const data = aboutData.about.skill

    const isLastChild = (itemIndex, itemList) => {
        return itemIndex === itemList.length - 1
    }
</script>

<template>
    <!-- <div class="skill section_big">
        <div class="container">
            <h2 class="section_title">我的專長</h2>
            <div class="item_box">
                <div class="item" v-for="item of data" :key="item.key">
                    <h3 class="subtitle">{{ item.title }}</h3>
                    <ul class="list_box">
                        <li class="list" v-for="listItem of item.list" v-html="listItem"></li>
                    </ul>
                </div>
            </div>
        </div>
    </div> -->
    <div class="skill section_big">
        <div class="container">
            <h2 class="section_title">我的專長</h2>
            <div class="list_box">
                <div class="list" v-for="(item, itemIndex) of data" :class="{ 'last': isLastChild(itemIndex, data)}" :key="itemIndex">
                    <div class="image_box">
                        <img class="image" :src="item.icon" width="60" height="60" alt="UI/UX Design">
                    </div>
                    <div class="text_box">
                        <h3 class="subtitle">{{ item.title }}</h3>
                        <ul class="listItem_box">
                            <li class="listItem" v-for="listItem of item.list" v-html="listItem"></li>
                        </ul>
                    </div>
                    
                </div>
            </div>
        </div>
    </div>
</template>

<style lang="scss">
    .skill {
        background: var(--main-light);
        .container {
            .title {
                color: var(--body-normal);
                padding-bottom: 5px;
            }
            .list_box {
                display: flex;
                padding: 80px 0 0 50px;
                justify-content: space-between;
                @include max-screen(991px) {
                    flex-direction: column;
                    padding: 80px 50px 0;
                }

                .list {
                    position: relative;
                    width: calc(50% - 60px);
                    padding: 45px 45px 30px;
                    border-radius: var(--border-radius);
                    background: var(--skill-list-bg);
                    margin-right: 90px;
                    @include max-screen(991px) {
                        width: 100%;
                        margin-bottom: 80px;
                        &:last-child {
                            margin-bottom: 0;
                        }
                    }
                    &.last {
                        margin-right: 0;
                    }
                    .image_box{
                        position: absolute;
                        display: flex;
                        align-items: center;
                        justify-content: center;
                        top: 0;
                        left: 0;
                        width: 100px;
                        height: 100px;
                        background: var(--skill-icon-bg);
                        border-radius: 100%;
                        transform: translate(-50%, -50%);
                    }
                    .subtitle{
                        padding-bottom: 5px;
                    }

                    .listItem_box {
                        padding-left: 30px;
                        .listItem {
                            list-style: disc;
                            color: var(--font-color);
                        }
                    }
                }
            }
        }
    }
    // .skill {
    //     background: var(--main-light);
    //     .container {
    //         .item_box {
    //             display: flex;
    //             padding: 0 30px;
    //         }
    //         .item {
    //             margin: 0 30px;
    //         }
    //         .subtitle {
    //             color: var(--body-normal);
    //             padding-bottom: 20px;
    //         }
    //         .list_box {
    //             padding-left: 30px;
    //             line-height: 1.8;
    //             .list {
    //                 list-style: disc;
    //                 color: var(--font-color);
    //             }
    //         }
    //     }
    // }
</style>

