
import type itemVue from '../ProjectList/item.vue';
<script setup>
    import aboutData from '~/assets/json/about.json'

    const data = aboutData.about.tool 
</script>

<template>
    <div class="software">
        <div class="container">
            <h2 class="section_title">軟體工具</h2>
            <div class="item_box">
                <div class="item" v-for="item of data" :key="item.key">
                    <h3 class="subtitle">{{ item.key }}</h3>
                    <div class="list_box">
                        <div class="list" v-for="( listItem, listIndex ) of item.list" :key="listIndex">
                            <div class="icon_box">
                                <img class="icon" :src="listItem.imgSrc" :alt="listItem.title">
                            </div>
                            <p class="text">{{ listItem.title }}</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<style lang="scss">
    .software {
        padding: 60px 0 90px;
        .subtitle {
            padding: 0 15px 15px;
        }
        .list_box {
            display: flex;
            flex-wrap: wrap;
            .list {
                margin: 0 13px 30px;
                @include max-screen(480px) {
                    width: calc(33.333333% - 26px);
                }
                .icon_box {
                    display: flex;
                    align-items: center;
                    justify-content: center;
                    margin: 0 auto;
                    width: 96px;
                    height: 96px;
                    border-radius: var(--border-radius);
                    background: var(--small-item-bg);
                    .icon {
                        max-height: 48px;
                    }
                }

                .text {
                    font-size: 12px;
                    font-weight: 500;
                    text-align: center;
                    padding-top: 10px;
                    color: var(--body-normal);
                }
            }
        }
    }
</style>

