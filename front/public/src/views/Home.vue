<template lang='pug'>
v-layout#Home(fill-height column)
    hello-world
    v-btn(@click='clicked') share
</template>

<script lang='ts'>
import { Component, Vue } from 'vue-property-decorator';
import HelloWorld from '@/components/HelloWorld.vue';

@Component({
    components: {
        HelloWorld,
    },
})
export default class Home extends Vue {
    protected async clicked() {
        try {
            await (navigator as any).share({
                title: 'Web Fundamentals',
                text: 'Check out Web Fundamentals — it rocks!',
                url: 'https://developers.google.com/web',
            });
            this.$vdialog.alert('Successful share');
        } catch (e) {
            this.$vdialog.alert(`Failed share: ${e.message}`);
        }
    }
}
</script>

<style lang='stylus'>
@require '~@/assets/styles/entry/_view.styl';

html
    scroll-view: true;
    // static-view: true;

#Home {}
</style>
