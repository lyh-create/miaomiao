<template>
  <div class="city_body">
        <div class="city_list">
            <div class="city_hot">
                <h2>热门城市</h2>
                <ul class="clearfix">
                    <li v-for="item in hotList" :key="item.id">{{item.name}}</li>
                </ul>
            </div>
            <div class="city_sort" ref="city_sort">
                <div  v-for="item in cityList" :key="item.id">
                    <h2>{{item.py.substring(0,1).toUpperCase()}}</h2>
                    <ul>
                        <li>{{item.name}}</li>
                    </ul>
                </div>	
            </div>
           
        </div>
        <div class="city_index">
            <ul>
                <li v-for="(item,index) in jList" :key="item.index" @touchstart="handleToIndex(index)">
                    {{item}}
                </li>
            </ul>
        </div>
  </div>
</template>

<script>
export default {
    name:'City',
    data(){
       return{
            cityList:[{
            "id":1,
            "name":"北京",
            "isHot":1,
            "py":"BeiJing"
        },{
            "id":2,
            "name":"上海",
            "isHot":1,
            "py":"ShangHai"
        },{
            "id":3,
            "name":"广州",
            "isHot":0,
            "py":"GuangZhou"
        },{
            "id":4,
            "name":"深圳",
            "isHot":0,
            "py":"ShenZhen"
        },{
            "id":5,
            "name":"邯郸",
            "isHot":1,
            "py":"HanDan"
        },{
            "id":6,
            "name":"大梁",
            "isHot":1,
            "py":"DaLiang"
        }],
        jList:[],
        hotList:[]
       }
    },
    mounted(){
        var {hotList,jList} = this.formatCityList()
        this.hotList = hotList
        this.jList = jList
    },
    methods:{
        formatCityList(){
            var hotList = [];
            var fList = [];
            var jList = [];
            var cityList = this.$data.cityList
            // 返回热门城市
            for(var i = 0;i<cityList.length;i++){
                if(cityList[i].isHot == 1){
                    hotList.push( cityList[i] );
                }
            }
            // console.log(hotList);
            for(var j = 0;j < cityList.length;j++){
                fList.push(cityList[j].py.substring(0,1).toUpperCase());
            }
            // console.log(fList.sort());
            fList = fList.sort()
            // console.log(fList);
            // 对排序后的字母数组去重
            for(var k in fList){
                if(jList.indexOf(fList[k])===-1){
                    jList.push(fList[k])
                }
            }
            // 返回排序后的字母数组
            // console.log(jList);
            return{
                hotList,
                jList
            }
        },
        handleToIndex(index){
            var h2 = this.$refs.city_sort.getElementsByTagName('h2');
            this.$refs.city_sort.parentNode.scrollTop = h2[index].offsetTop;
            // this.$refs.city_List.toScrollTop(-h2[index].offsetTop);
        }
    },
}
</script>

<style scoped>
#content .city_body{ margin-top: 45px; display: flex; width:100%; position: absolute; top: 0; bottom: 0;}
.city_body .city_list{ flex:1; overflow: auto; background: #FFF5F0;}
.city_body .city_list::-webkit-scrollbar{
    background-color:transparent;
    width:0;
}
.city_body .city_hot{ margin-top: 20px;}
.city_body .city_hot h2{ padding-left: 15px; line-height: 30px; font-size: 14px; background:#F0F0F0; font-weight: normal;}
.city_body .city_hot ul li{ float: left; background: #fff; width: 29%; height: 33px; margin-top: 15px; margin-left: 3%; padding: 0 4px; border: 1px solid #e6e6e6; border-radius: 3px; line-height: 33px; text-align: center; box-sizing: border-box;}
.city_body .city_sort div{ margin-top: 20px;}
.city_body .city_sort h2{ padding-left: 15px; line-height: 30px; font-size: 14px; background:#F0F0F0; font-weight: normal;}
.city_body .city_sort ul{ padding-left: 10px; margin-top: 10px;}
.city_body .city_sort ul li{ line-height: 30px; line-height: 30px;}
.city_body .city_index{ width:20px; display: flex; flex-direction:column; justify-content:center; text-align: center; border-left:1px #e6e6e6 solid;}
</style>