<template>
    <div class='setting'>
        <header>
            <i class="el-icon-arrow-left" @click.stop='back'></i>
        </header>
        <section>
            <div class='item' @click='comments'>
                <div>{{$t('lang.score')}}</div>
                <div><i class="el-icon-arrow-right"></i></div>
            </div>
            <div class='item' @click='issues'>
                <div>{{$t('lang.bug')}}</div>
                <div><i class="el-icon-arrow-right"></i></div>
            </div>
            <div class='item' @click='seeCode'>
                <div>{{$t('lang.source')}}</div>
                <div><i class="el-icon-arrow-right"></i></div>
            </div>
            <div class='item' @click='goLibrary'>
                <div>{{$t('lang.lib')}}</div>
                <div><i class="el-icon-arrow-right"></i></div>
            </div>
            <div class='item'>
                <div>{{$t('lang.ver')}}  {{version}}</div>
                <div><i class="el-icon-arrow-right"></i></div>
            </div>
        </section>
    </div>
</template>
<script>
export default {
  data: () => {  
    return{
       version:''
    }
  },
  created(){
      this.version = chrome.runtime.getManifest().version
  },
  props: {
    data: { 
      default: function() {
        return ''
      }
    },
    showSettingHandle:{
      default:()=>{}
    }
  },
  methods:{
      back(){
          this.$emit('hideSettingHandle');
      },
      handleChange(val) {
        // console.log(val);
      },
      seeCode(){
          window.open('https://github.com/llqi/oh-my-cookie')
      },
      issues(){
          window.open('https://github.com/llqi/oh-my-cookie/issues')
      },
      goLibrary(){
          window.open('https://github.com/YuraDev/vue-chrome-extension-template')
      },
      comments(){
          window.open('https://chrome.google.com/webstore/detail/ohmycookie/edkfjjgklckogiepbhmmdlaohebiaigm?hl=zh-CN')
      }
  }
}
</script>
<style lang='scss'>
.setting{
    
    header{
        padding-top:10px;
        padding-left:4px;
        .el-icon-arrow-left{
            font-size: 25px;
            cursor: pointer;
        }
    }   
    section{
        padding:10px 10px 10px;
        .item{
            width:100%;
            height:45px;
            border-bottom: 1px solid #EBEEF5;
            background-color: #FFF;
            display:flex;
            justify-content: space-between;
            line-height: 45px;
            font-size: 16px;
            cursor: pointer;
            color:#606266;
        }
    }
}
</style>
