# html tab组件说明 #
	<view class="container999">
	<navTab ref="navTab" :tabTitle="tabTitle" @changeTab='changeTab'></navTab>
	<view>
	    //script
	    // 引入tab
	    import navTab from "../../components/navTab.vue"
	    export default {
	    components: {
	    navTab
	    },
	    data() {
	    return {
	    currentTab: 0, //sweiper所在页
	    tabTitle:['选择一','选择二','选择三','选择四'], //导航栏格式
	    }
	    },
	    methods:{
	    // tab事件
	    	changeTab(index){
	    			this.currentTab = index;
	    		},
	    // swiper 滑动 如果tab关联swiper需要写下面的方法 否则不写
	    swiperTab: function(e) {
	    			var index = e.detail.current //获取索引
	    			this.$refs.navTab.longClick(index);
	    		},
	    }
	    };
			    
# html 下拉刷新组件说明  #		
			//最外层加上touch事件
			//刷新组件需搭配scroll-view使用，并在pages.json中添加 "disableScroll":true
    		<viewclass="container999" 
    			@touchstart="refreshStart" 
    			@touchmove="refreshMove" 
    			@touchend="refreshEnd"
    		<refresh ref="refresh" @isRefresh='isRefresh'></refresh>
    		</view>
    		//script
    		// 引入下拉刷新
    		import refresh from '../../components/refresh.vue';
    		export default {
    		components: {refresh},
    		data() {
    		return {
    		
    		};
    		},
    		methods: {
    		refreshStart(e) {
    		this.$refs.refresh.refreshStart(e);
    		},
    		refreshMove(e){
    		this.$refs.refresh.refreshMove(e);
    		},
    		refreshEnd(e) {
    		this.$refs.refresh.refreshEnd(e);
    		},
    		//刷新名需写为isRefresh,刷新组件中会回调此事件
    		   	isRefresh(){
    					setTimeout(() => {
    					uni.showToast({
    					icon: 'success',
    					title: '刷新成功'
    					})
    					this.$refs.refresh.endAfter() //刷新结束调用
    					}, 1000)
    				}
    		}
    		};