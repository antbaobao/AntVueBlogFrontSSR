<template>
    <div class="archives">
        <p class="archives__title">文章归档</p>
        <p />
        <ul class="archives__items-container">
            <li
                v-for="item in archives"
                :key="item._id"
                class="archives__item"
            >
                <a
                    class="archives__item-info"
                    @click="$router.push({ path: `/archive/${item._id}` })"
                >
                    {{ item._id}} ({{item.count}})
                </a>
            </li>

        </ul>
    </div>
</template>
<script>
import { timeAgo } from '@/util/filters'

export default {
    name: 'archives',
    computed: {
        archives() {
            return this.$store.state.home.archives
        },
    }
}
</script>
<style lang="stylus" scoped>
.archives
    padding 20px
    border-radius 5px
    border 1px solid transparent
    box-shadow 0px 1px 3px #888
    .archives__title
        font-size 20px
    .archives__items-container
        margin 0
        padding 0
        .archives__item
            float left
            width 50%
            list-style-type square
            color: #828282
            font-size: 0.9em
            padding 5px 0
@media (max-width 1600px)
    .archives
        margin-top 45px
@media (max-width: 960px)
    .archives
        box-shadow none
.archives:after
    content ''
    display block
    clear both
.archives__item-info
    cursor pointer

</style>
