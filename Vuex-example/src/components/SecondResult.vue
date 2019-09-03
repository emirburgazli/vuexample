<template>
    <div>
        <p class="counter-container"> Sayaç : {{ double }}</p>
        <p class="counter-container"> Tıklama sayısı : {{ stringC }}</p>
        <input type="text" v-model="value">
        <p> {{ value }}</p>
    </div>
</template>
<script>
    import {mapGetters} from "vuex";

    export default {
        // props: ["counter"],

        // 1.YOL

        // computed: mapGetters([
        //     'getDoubleCounter',
        //     'stringCounter'
        // ])

        // 2.YOL

        computed: {
            ...mapGetters({
                double: 'getDoubleCounter',
                stringC: 'stringCounter'
            }),
            value: {
                get() {
                    return this.$store.getters.getValue;
                },
                set(value) {
                    this.$store.dispatch("setValueData", value)
                }
            }
        },
    }

</script>
<style scoped>
    .counter-container {
        border: 1px solid #fbbd08;
        padding: 10px 5px;
        background-color: #fbbd08;
        font-size: 20px;
        color: #000;
    }
</style>
