<template> 
<div class="bg-gray-100"> 
    <div class="container w-full mx-auto">
        <div class="w-full px-4 md:px-0 md:mt-8 mb-16 text-gray-800 leading-normal">

            <v-container>
                <h2 class="font-bold text-3xl"><i class="em em-herb text-4xl" aria-role="presentation" aria-label=""></i> &nbsp; ส่งออกข้อมูลควาย</h2> 
                <v-breadcrumbs :items="bc" large>
                    <template v-slot:divider>
                        <v-icon>mdi-chevron-right</v-icon>
                    </template>
                </v-breadcrumbs>
                <hr class="border-b-2 border-gray-400 ">
            </v-container>
             
            <div class="flex flex-wrap">
                <div class="w-full md:w-1/1 xl:w-1/1 p-0 md:p-3 mb-3"> 
                    <div class="bg-white border-b-4 border-pink-700 rounded shadow-xl p-2">
                        <div class="flex flex-col md:flex-row items-center">
                            <v-expansion-panels flat>
                                <v-expansion-panel>
                                    <v-expansion-panel-header class="font-bold ">
                                        <div class="text-xl">ค้นหา</div>
                                    </v-expansion-panel-header>

                                    <v-expansion-panel-content>
                                        <div class="flex flex-row flex-wrap">
                                            <v-text-field dense class="pa-1" v-model="search" clearable flat hide-details append-icon="mdi-magnify" label="ค้นหา" outlined single-line></v-text-field>
                                            <v-select outlined dense class="pa-1" :items="province" label="กรุณาเลือกจังหวัด" hide-details></v-select>
                                            <v-select outlined dense class="pa-1" :items="aumphur" label="กรุณาเลือกอำเภอ" hide-details></v-select>
                                            <v-select outlined dense class="pa-1" :items="tumbon" label="กรุณาเลือกตำบล" hide-details></v-select>
                                            <v-select outlined dense class="pa-1" :items="group" label="กรุณาเลือกกลุ่มเกษตกร" hide-details></v-select>
                                            <v-btn depressed class="ma-1 d-sm-block" color="blue" @click="$router.push('/')" dense dark>
                                                <v-icon>mdi-magnify</v-icon>ค้นหา
                                            </v-btn>
                                            <v-btn depressed color="success" medium dense dark class="ma-1">ส่งออกรายงาน</v-btn> 
                                        </div>
                                    </v-expansion-panel-content>
                                </v-expansion-panel>
                            </v-expansion-panels>
                        </div>
                    </div>
 
                </div>

                <div class="w-full md:w-1/1 xl:w-1/1 p-0 md:p-3 mb-3">
                    <v-data-table class="bg-white border-b-4 border-pink-700 rounded shadow-xl p-2" dense :headers="headers" :items="desserts" :search="search" sort-by="calories">

                        <template v-slot:no-data>
                            <v-btn color="primary" @click="initialize">Reset</v-btn>
                        </template>
                    </v-data-table>
                </div>
            </div>
        </div>
    </div>
</div>
</template>

<script>
export default {
    data: () => ({
        bc: [{
                text: 'แดชบอร์ด',
                disabled: false,
                href: '/#/admin/home',
            },
            {
                text: 'ส่งออกข้อมูลควาย',
                disabled: false,
                href: '/#/admin/export',
            },
        ],
        tumbon: ['แม่กา', 'แม่ใจ'],
        group: ['กลุ่มแม่กา', 'กลุ่มแม่ใจ'],
        aumphur: ['เมือง'],
        province: ['พะเยา', 'เชียงราย', 'แพร่', 'น่าน'],
 
        headers: [{
                text: 'เลขบัตรประชาชน',
                value: 'IDCard',
                sortable: false
            },
            {
                text: 'ชื่อ',
                value: 'name',
                sortable: false
            },
            {
                text: 'จำนวนกระบือทั้งหมด',
                value: 'Phonenumber',
                sortable: false
            },
            {
                text: 'จำนวนกระบือายุ 240 วัน',
                value: 'age240',
                sortable: false
            },
            {
                text: 'จำนวนกระบือายุ 400 วัน',
                value: 'age400',
                sortable: false
            },
            {
                text: 'จำนวนกระบือายุ 600 วัน',
                value: 'age600',
                sortable: false
            },
            {
                text: 'ตำบล',
                value: 'tumbon',
                sortable: false
            },
            {
                text: 'อำเภอ',
                value: 'aumphur',
                sortable: false
            },
            {
                text: 'จังหวัด',
                value: 'province',
                sortable: false
            },
            {
                text: 'กลุ่มผู้ใช้',
                value: 'group',
                sortable: false
            },
            
        ],
        desserts: [],
      
    }),

    computed: {

    },

    watch: {
 
    },

    created() {
        this.initialize()
    },

    methods: {
        initialize() {
            this.desserts = [{
                    IDCard: 1234567890123,
                    name: 'นายแดง แดงแดง',
                    Phonenumber: '0911231231',
                    group: 'กลุ่มแม่ใจ',
                },
                {
                    IDCard: 3123412345612,
                    name: 'นายดำ ดำดำ',
                    Phonenumber: '0914123412',
                    group: 'กลุ่มแม่ใจ',
                },
                {
                    IDCard: 1231241231233,
                    name: 'นายเขียว เขียวเขียว',
                    Phonenumber: '0812312312',
                    group: 'กลุ่มพาน',
                },
                {
                    IDCard: 1111111111111,
                    name: 'นายเขียว เขียวขจี',
                    Phonenumber: '0822312312',
                    group: 'กลุ่มพาน',
                },
                {
                    IDCard: 2222222222222,
                    name: 'นายเหลือง เหลืองเหลือง',
                    Phonenumber: '0833333333',
                    group: 'กลุ่มแม่กา',
                },
                {
                    IDCard: 3333333333333,
                    name: 'นายชัย',
                    Phonenumber: '0844444444',
                    group: 'กลุ่มแม่กา',
                },
                {
                    IDCard: 4444444444444,
                    name: 'นายใหญ่',
                    Phonenumber: '0855555555',
                    group: 'กลุ่มพะเยา',
                },
                {
                    IDCard: 5555555555555,
                    name: 'นายเล็ก',
                    Phonenumber: '0866666666',
                    group: 'กลุ่มพะเยา',
                },
                {
                    IDCard: 6666666666666,
                    name: 'นายคำ',
                    Phonenumber: '0877777777',
                    group: 'กลุ่มพะเยา',
                },
                {
                    IDCard: 7777777777777,
                    name: 'นายนาย',
                    Phonenumber: '0888888888',
                    group: 'กลุ่มพะเยา',
                },

            ]
        },

    },
}
</script>
