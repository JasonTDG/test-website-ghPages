<script setup>
    import aboutData from '~/assets/json/about.json'

    const data = aboutData.about.experience

    const isLastChild = (itemIndex, itemList) => {
        return itemIndex === itemList.length - 1
    }

</script>

<template>
    <div class="experience">
        <div class="container">
            <h2 class="section_title">工作經驗</h2>
            <div class="list_box" v-for="(item, itemIndex) of data" :key="itemIndex">
                <div class="list" :class="{ 'last-child': isLastChild(itemIndex, data)}">
                    <h3 class="subtitle">{{ item.title }}</h3>
                    <div class="company">
                        <p class="name">{{ item.company }}</p>
                        <p class="time">{{ item.time }}</p>
                    </div>
                    <!-- <p class="text" v-for="(listItem, listIndex) of item.list"  :key="listIndex" v-html="listItem"></p> -->
                    <ul class="listItem_box">
                        <li class="listItem" v-for="(listItem, listIndex) of item.list"  :key="listIndex" v-html="listItem"></li>
                    </ul>
                </div>
            </div>
        </div>
    </div>
</template>

<style lang="scss">
    .experience {
        padding: 90px 0;
        .title {
            color: var(--body-normal);
            margin-bottom: 30px;
        }

        .list_box {
            .list {
                position: relative;
                padding-bottom: 30px;
                padding-left: 80px;

                @include max-screen(768px) {
                    padding-left: 50px;
                }

                @include max-screen(480px) {
                    padding-left: 30px;
                }

                &::before {
                    content: '';
                    position: absolute;
                    top: 10px;
                    left: 20px;
                    width: 10px;
                    height: 10px;
                    border-radius: 20px;
                    background-color: var(--highlight);

                    @include max-screen(480px) {
                        left: 5px;
                    }
                }

                &::after {
                    content: '';
                    position: absolute;
                    top: 10px;
                    left: 25px;
                    width: 1px;
                    height: 100%;
                    background-color: var(--highlight);

                    @include max-screen(480px) {
                        left: 10px;
                    }
                }

                &.last-child {
                    padding-bottom: 0;

                    &::after {
                        display: none;
                    }
                }

                // &:last-child {
                //     padding-bottom: 0;

                //     &::after {
                //         display: none;
                //     }
                // }

                .subtitle {
                    font-weight: 500;
                    margin-bottom: 15px;
                    color: var(--body-normal);
                }

                .company {
                    display: flex;
                    font-weight: 500;
                    margin-bottom: 5px;

                    @include max-screen(480px) {
                        flex-direction: column;
                    }

                    .name {
                        position: relative;
                        color: var(--body-normal);
                        padding-right: 15px;
                        margin-right: 15px;
                        &::before {
                            content: '';
                            position: absolute;
                            top: 50%;
                            right: 0;
                            width: 1px;
                            height: 15px;
                            transform: translateY(-50%);
                            background-color: var(--body-normal);

                            @include max-screen(480px) {
                                display: none;
                            }
                        }
                    }

                    .time {
                        color: var(--body-normal);
                    }
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
        .text {
            color: var(--font-color);
        }
    }
</style>

