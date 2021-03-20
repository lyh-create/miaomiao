<template>
    <div class="movie_body" ref="movie_body">
        <!-- <Loading v-if="isLoading" /> -->
        <Scroller  :handleToTouchEnd="handleToTouchEnd">
             <ul>
                <li class="pullDown">{{ pullDownMsg }}</li>
                <li v-for="item in movieList" :key="item.index">
                    <div class="pic_show" @tap="handleToDetail"><img :src="item.img"></div>
                    <div class="info_list">
                        <h2>{{item.name}}<img v-if="item.version" src="@/assets/maxs.png" alt=""></h2>
                        <p>观众评 <span class="grade">{{item.star}}</span></p>
                        <p>主演:{{item.star}}</p>
                        <p>{{item.showInfo}}</p>
                    </div>
                    <div class="btn_mall">
                        购票
                    </div>
                </li>
                <!-- <li class="pullDown">{{ pullDownMsg }}</li>
                <li v-for="item in movieList" :key="item.id">
                    <div class="pic_show" @tap="handleToDetail(item.id)"><img :src="item.img | setWH('128.180')"></div>
                    <div class="info_list">
                        <h2 @tap="handleToDetail(item.id)">{{ item.nm }} <img v-if="item.version" src="@/assets/maxs.png" alt=""></h2>
                        <p>观众评 <span class="grade">{{ item.sc }}</span></p>
                        <p>主演: {{ item.star }}</p>
                        <p>{{ item.showInfo }}</p>
                    </div>
                    <div class="btn_mall">
                        购票
                    </div>
                </li> -->
            </ul>
        </Scroller>
    </div>
</template>

<script>

export default {
    name:'NowPlaying',
    data(){
        return{
             movieList:[{
                img:'/images/movie_1.jpg',
                name:'无名之辈',
                score:9.2,
                star:'陈建斌,任素汐,潘斌龙',
                showInfo:'今天55家影院放映607场',
                version:'3ds max'
            },{
                img:'/images/movie_2.jpg',
                name:'毒液',
                score:9.0,
                star:'汤姆·哈迪，米歇尔·威廉姆斯，里兹·阿迈耶',
                showInfo:'2018-11-30上映',
                version:''
            },{
                img:'/images/movie_1.jpg',
                name:'无名之辈',
                score:9.2,
                star:'陈建斌,任素汐,潘斌龙',
                showInfo:'今天55家影院放映607场',
                version:'3ds max'
            },{
                img:'/images/movie_2.jpg',
                name:'毒液',
                score:9.0,
                star:'汤姆·哈迪，米歇尔·威廉姆斯，里兹·阿迈耶',
                showInfo:'2018-11-30上映',
                version:''
            },{
                img:'/images/movie_1.jpg',
                name:'无名之辈',
                score:9.2,
                star:'陈建斌,任素汐,潘斌龙',
                showInfo:'今天55家影院放映607场',
                version:'3ds max'
            },{
                img:'/images/movie_2.jpg',
                name:'毒液',
                score:9.0,
                star:'汤姆·哈迪，米歇尔·威廉姆斯，里兹·阿迈耶',
                showInfo:'2018-11-30上映',
                version:''
            }],
            pullDownMsg:'',
            // isLoading:true
        }
    },
    methods : {
        handleToDetail(movieId){
            //console.log(movieId);
            this.$router.push('/movie/detail/1/' + movieId);
        },
        handleToScroll(pos){
            if( pos.y > 30 ){
                this.pullDownMsg = '正在更新中';
            }
        },
        handleToTouchEnd(pos){
            if( pos.y > 30 ){
                this.pullDownMsg = '更新成功';
                setTimeout(()=>{
                    this.pullDownMsg = '';
                },1000);
            }
        }
    }
}
</script>

<style>
#content .movie_body{ flex:1; overflow:auto;}
.movie_body ul{ margin:0 12px; overflow: hidden;}
.movie_body ul li{ margin-top:12px; display: flex; align-items:center; border-bottom: 1px #e6e6e6 solid; padding-bottom: 10px;}
.movie_body .pic_show{ width:64px; height: 90px;}
.movie_body .pic_show img{ width:100%;}
.movie_body .info_list { margin-left: 10px; flex:1; position: relative;}
.movie_body .info_list h2{ font-size: 17px; line-height: 24px; width:150px; overflow: hidden; white-space: nowrap; text-overflow:ellipsis;}
.movie_body .info_list p{ font-size: 13px; color:#666; line-height: 22px; width:200px; overflow: hidden; white-space: nowrap; text-overflow:ellipsis;}
.movie_body .info_list .grade{ font-weight: 700; color: #faaf00; font-size: 15px;}
.movie_body .info_list img{ width:50px; position: absolute; right:10px; top: 5px;}
.movie_body .btn_mall , .movie_body .btn_pre{ width:47px; height:27px; line-height: 28px; text-align: center; background-color: #f03d37; color: #fff; border-radius: 4px; font-size: 12px; cursor: pointer;}
.movie_body .btn_pre{ background-color: #3c9fe6;}
.movie_body .pullDown{ margin:0; padding:0; border:none;}
</style>