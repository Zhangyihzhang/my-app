<template>
  <!-- 头部 -->
  <header class="header">
    <!-- 头部的第一行 -->
    <div class="top">
      <div class="container">
        <div class="loginList">
          <p>尚品汇欢迎您！</p>
          <p>
            <span>请</span>
            <a href="###">登录</a>
            <a href="###" class="register">免费注册</a>
          </p>
        </div>
        <div class="typeList">
          <a href="###">我的订单</a>
          <a href="###">我的购物车</a>
          <a href="###">我的尚品汇</a>
          <a href="###">尚品汇会员</a>
          <a href="###">企业采购</a>
          <a href="###">关注尚品汇</a>
          <a href="###">合作招商</a>
          <a href="###">商家后台</a>
        </div>
      </div>
    </div>
    <!--头部第二行 搜索区域-->
    <div class="bottom">
      <h1 class="logoArea">
        <a class="logo" title="尚品汇" href="###" target="_blank">
          <img src="./images/logo.png" alt />
        </a>
      </h1>
      <div class="searchArea">
        <form action="###" class="searchForm">
          <input type="text" id="autocomplete" class="input-error input-xxlarge" v-model="keyWord" />
          <button class="sui-btn btn-xlarge btn-danger" type="button" @click="goSearch">搜索</button>
        </form>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  name: "",
  data() {
    return {
      //响应式数据，用于收集表单元素文本内容
      keyWord: "",
    };
  },
  methods: {
    //搜索按钮的事件处理函数，用于跳转到search路由组件当中
    goSearch() {
      //代表的是如果有query参数也带过去
      if (this.$route.query) {
        let loction = {
          name: "search",
          params: { keyWord: this.keyWord || undefined },
        };
        loction.query = this.$route.query;
        this.$router.push(loction);
      }
    },
    //   //退出登录
    //   async logout() {
    //     //退出登录需要做的事情
    //     //1:需要发请求，通知服务器退出登录【清除一些数据：token】
    //     //2:清除项目当中的数据【userInfo、token】
    //     try {
    //       //如果退出成功
    //       await this.$store.dispatch("userLogout");
    //       //回到首页
    //       this.$router.push("/home");
    //     } catch (error) {}
    //   },
    // },
    // mounted() {
    //   //通过全局事件总线清除关键字
    //   this.$bus.$on("clear", () => {
    //     this.keyword = "";
    //   });
    // },
    // computed: {
    //   //用户名信息
    //   userName() {
    //     return this.$store.state.user.userInfo.name;
    //   },
  },
};
</script>

<style scoped lang="less">
.header {
  & > .top {
    background-color: #eaeaea;
    height: 30px;
    line-height: 30px;

    .container {
      width: 1200px;
      margin: 0 auto;
      overflow: hidden;

      .loginList {
        float: left;

        p {
          float: left;
          margin-right: 10px;

          .register {
            border-left: 1px solid #b3aeae;
            padding: 0 5px;
            margin-left: 5px;
          }
        }
      }

      .typeList {
        float: right;

        a {
          padding: 0 10px;

          & + a {
            border-left: 1px solid #b3aeae;
          }
        }
      }
    }
  }

  & > .bottom {
    width: 1200px;
    margin: 0 auto;
    overflow: hidden;

    .logoArea {
      float: left;

      .logo {
        img {
          width: 175px;
          margin: 25px 45px;
        }
      }
    }

    .searchArea {
      float: right;
      margin-top: 35px;

      .searchForm {
        overflow: hidden;

        input {
          box-sizing: border-box;
          width: 490px;
          height: 32px;
          padding: 0px 4px;
          border: 2px solid #ea4a36;
          float: left;

          &:focus {
            outline: none;
          }
        }

        button {
          height: 32px;
          width: 68px;
          background-color: #ea4a36;
          border: none;
          color: #fff;
          float: left;
          cursor: pointer;

          &:focus {
            outline: none;
          }
        }
      }
    }
  }
}
</style>
