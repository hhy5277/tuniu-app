<template>
    <div class="icons border-bottom">
        <swiper :options="Option">
            <swiper-slide v-for="(page, index) in pages" :key="index">
                <div class="icon" v-for="item of page" :key="item.id">
                    <div class="icon-img">
                        <img class="icon-img-content" :src="item.imgUrl">
                    </div>
                    <div class="icon-keywords">{{item.desc}}</div>
                </div>
            </swiper-slide>
        </swiper>
    </div>
</template>
<script>
export default {
    name: 'tIcon',
    props: {
        iconList: {
            type: Array
        }
    },
    data () {
        return {
             Option: {
                autoplay : false
            }
        }
    },
    computed: {
        pages () {
            const pages = []
            this.iconList.forEach( (item, index) => {
                const page = Math.floor(index / 5)
                if(!pages[page]) {
                    pages[page] = []
                }
                pages[page].push(item)
            })
            return pages
        }
    }
}
</script>
<style lang="stylus" scoped>
@import '~styles/varibles'
@import '~styles/mixin'
.icons >>> .swiper-container
    height 0
    padding-bottom 25%
.icons
    background #fff
    padding  .25rem 0
    .icon
        float left
        width 20%
        height 4rem
        .icon-img
            box-sizing: border-box
            padding: .25rem
            .icon-img-content
                width 2.4rem
                display block
                margin 0 auto
                height 2.4rem
        .icon-keywords
            left: 0
            right: 0
            bottom: 0
            height: 1.1rem
            font-size $fontSize
            line-height: 1.1rem
            text-align: center
            color: $darkTextColor
            ellipsis()
</style>


