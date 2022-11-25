<template>
  <div class="test">
    <span>商品规格</span>
    <br>
    <div id="spec">
        <input v-model="Specifications"><button @click="add">添加子规格</button><button @click="del()">删除</button>
        <div v-show="listData" v-for="(item, index) in listData" :key="index">
            <input><button @click="delspec(item, index)">删除</button>
        </div>
    </div>
    <br>
    <div>
    <input v-model="Specifications2"><button @click="add2">添加子规格</button><button @click="del2()">删除</button>
    <div v-show="listData1" v-for="(item, index) in listData1" :key="index">
            <input><button @click="delspec1(item, index)">删除</button>
        </div>
    </div>
    <table border="1">
        <tr>
            <th>主图</th><th>规格名称</th><th>规格编码</th><th>市场价</th><th>会员</th><th>果粉</th><th>合伙人</th><th>联创</th><th>成本价</th>
        </tr>
        <tr v-for="(item, index) in tableList" :key="index">
            <td><span>123</span></td>
            <td><div>{{item.open_type}}</div></td>
            <td><input type="checkbox">启用</td>
        </tr>
    </table>
  </div>
</template>

<script>

export default {
    name: 'configList',
    data() {
        return{
            listData:[],
            listData1:[],
            Specifications: '规格',
            Specifications2: '规格2',
            specList: [],
            tableList: [],
            listLeng: null,
            listLeng1: null
        }
    },
    mounted() {
        // this.getList()
        // this.sendAjax()
    },
    methods:{
        add() {
            // let spec = document.getElementsById('spec')
            this.listData.push({key: 'num', value: ''})
        },
        del(item, index) {
            console.log(item,index)
            this.listData = []
        },
        add2() {
            this.listData1.push({key: 'num', value: ''})
        },
        del2(item, index) {
            console.log(item,index)
            this.listData1 = []
        },
        delspec(item, index) {
            console.log(item, index)
            this.listData.splice(index, 1)
        },
        delspec1(item, index) {
            console.log(item, index)
            this.listData1.splice(index, 1)
        }
        // sendAjax(){
        //     // return new Promise((resolve,reject) => {
        //         const xhr = new XMLHttpRequest()
        //         xhr.open('GET','https://api-hmugo-web.itheima.net/api/public/v1/home/swiperdata')
        //         xhr.send()
        //         let _this = this
        //         xhr.onreadystatechange = function() {
        //             if(xhr.readyState === 4) {
        //                 if(xhr.status >= 200 && xhr.status < 300) {
        //                     // resolve(xhr.response)
        //                     let arr = JSON.parse(xhr.response)
        //                     _this.listData = arr.message
        //                 } else {
        //                     // reject()
        //                 }
        //             }
        //         }
        //     // })
        // },
        // getList() {
        //     this.sendAjax('https://api-hmugo-web.itheima.net/api/public/v1/home/swiperdata').then(res => {
        //         let arr = JSON.parse(res)
        //         this.listData = arr.message
        //     })
        // },
        // makeList(){
        //     console.log('make')
        // }
    },
    watch:{
        listData:{
            handler:function(val) {
                if(val.length < 1 && this.listData1.length > 0) {
                    this.tableList = this.listData1
                }else{
                    this.listLeng = val.length
                    let num = this.listLeng * this.listLeng1
                    if(this.listLeng1) {
                        this.tableList = Array(num).fill({key: '', value: ''})
                    }else{
                    this.tableList = this.listData
                    }
                }
            }
        },
        listData1:{
            handler:function(val) {
                if(val.length < 1 && this.listData.length > 0) {
                    this.tableList = this.listData
                }else{
                    this.listLeng1 = val.length
                    let num = this.listLeng * this.listLeng1
                    if(this.listLeng) {
                        this.tableList = Array(num).fill({key: '', value: ''})
                    }else{
                        this.tableList = this.listData1
                    }
                }
            }
        }
    }
}
</script>

<style>

</style>