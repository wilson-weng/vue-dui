<template>
    <a :class="className" :href="href" @click="vLinkClickHandle">
        <span class="group-item-header" v-if="_slotContents.header">
            <slot name="header"></slot>
        </span>
        <span class="group-item-body">
            <slot></slot>
        </span>
        <span class="group-item-footer">
            <slot name="footer"></slot>
        </span>
        <template v-else>
        </template>
        <i class="fa fa-angle-right fa-right text-muted" v-if="(href || vLink || _events.click) && !unclickable"></i>
    </a>
</template>

<script>
    export default {
        props: {
            href: {
                type: String
            },
            vLink: {
                type: Object
            },
            class: {
                type: String,
            },
            pure: {
                type: Boolean,
                default: false
            },
            unclickable: {
                type: Boolean,
                default: false
            },
            related: {
                type: Boolean,
                default: false
            }
        },
        computed: {
            className(){
                let result = ['group-item', 'flexbox', 'flex-align-center'];
                //自定义class
                this.class && (result = result.concat(this.class.split(' ')));
                //关联Item
                this.related && (result.push('group-item-related'));
                //不带样式
                this.pure && result.push('group-item-pure');
                return result;
            }
        },
        methods: {
            //v-link点击事件
            vLinkClickHandle(){
                this.vLink && this.$route.router.go(this.vLink);
            }
        }
    }
</script>