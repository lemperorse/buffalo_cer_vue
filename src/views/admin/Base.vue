<template>
<v-app>
    <navbaradmin name="ผู้ดูแลระบบ" />

    <v-main>
        <notifications group="foo" position="bottom right" classes="p-6 m-4 text-white rounded-xl shadow" />
        <router-view />
    </v-main>
</v-app>
</template>

<script>
import navbaradmin from '@/components/admin/navbaradmin';
export default {
    name: 'Root',
    /*-------------------------ประกาศ components ---------------------------------------*/
    components: {
        navbaradmin
    },
    /*-------------------------รับค่าเมื่อเราเป็น components---------------------------------------*/
    props: {

    },
    /*-------------------------ประกาศตัวแปรที่ใช้ ผูกกับ v-model ---------------------------------------*/
    data() {
        return {

            txt: 'Hello World'

        };
    },
    /*------------------------- สิ่งทที่อยู่ในนี้จะถูกรัยเมื่อโหลด ------------------------------------------*/
    created: async function () {
        /**** เรียกใช้ methods ชื่อ load() */
        await this.load();
    },
    /*------------------------- กระทำการตอน router ถูกโหลดเข้ามา------------------------------------------*/
    async beforeRouteEnter(to, from, next) {
        next()
    },
    /*-------------------------ใช้จัดการ operation  หรือ คำนวณค่าต่างๆ (คล้าย methods)------------------------------------------*/
    computed: {

    },
    /*-------------------------Methods------------------------------------------*/
    methods: {
        /******* Methods default run ******/
        load: async function () {
            await this.$store.dispatch('core/checkToken');
            console.log(await this.$store.dispatch('auth/getPermissionRoute'));
        }
    },
}
</script>

<style lang='postcss' scoped>

</style>
