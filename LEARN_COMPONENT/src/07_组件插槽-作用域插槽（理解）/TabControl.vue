<!--  -->
<template>
    <div class='tab-control'>
        <template v-for="  (item, index) in titles" :key="index">
            <div @click="itemClick(index)" :class="{ active: index === currentIndex }" class="tab-control-item">
                <slot :item="item">
                    <span>{{ item }}</span>
                </slot>

            </div>

        </template>

    </div>
</template>

<script>

export default {
    emits: ['tabItemClick'],
    props: {
        titles: {
            type: Array,
            defalt: () => []
        }
    },
    data() {
        //这里存放数据
        return {
            currentIndex: 0,
        };
    },
    //监听属性 类似于data概念
    computed: {},
    //监控data中的数据变化
    watch: {},
    //方法集合
    methods: {
        itemClick(index) {
            this.currentIndex = index;
            console.log(this.currentIndex);
            this.$emit('tabItemClick', index)
        }
    },
    //生命周期 - 创建完成（可以访问当前this实例）
    created() {

    },
    //生命周期 - 挂载完成（可以访问DOM元素）
    mounted() {

    },
    //beforeCreate() {}, //生命周期 - 创建之前
    //beforeMount() {}, //生命周期 - 挂载之前
    //beforeUpdate() {}, //生命周期 - 更新之前
    //updated() {}, //生命周期 - 更新之后
    //beforeDestroy() {}, //生命周期 - 销毁之前
    //destroyed() {}, //生命周期 - 销毁完成
    //activated() {}, //如果页面有keep-alive缓存功能，这个函数会触发
}
</script>
<style scoped>
/* @import url()引入公共css类 */
.tab-control {
    display: flex;
    height: 44px;
    line-height: 44px;
    text-align: center;
}

.tab-control-item {
    flex: 1;
}

.tab-control-item.active {
    color: red;
}
</style>