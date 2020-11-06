<template>
  <div class="body_content">
    <div class="flexBox">
      <div class="logo"><img src="https://cdn.schoolpal.cn/schoolpal/resource/ci/SchoolPal-NETCore-PC/130/common/images/icon-loginlogo-new.jpg?version=20201022223932"></img></div>
      <div class="logo-right">
        <div class="logo-right-chid">公众号</div>
        <div class="logo-right-chid">帮助</div>
        <div class="logo-right-chid">周边</div>
        <div class="logo-right-chid">官网</div>
        <div class="logo-right-chid">申请使用</div>
      </div>
    </div>
    <div class="context">
      <div class="context-left"><img src=" https://schoolpal.oss-cn-hangzhou.aliyuncs.com/erpbanner/erplogin0827.jpg"></img></div>
      <div class="context-right">
        <div class="left_one">
          <div id="ph">
            <router-link to="/" tag="div">手机号码登录</router-link>
          </div>
          <div id="zh">
            <router-link to="/other" tag="div">账号登录</router-link>
          </div>
        </div>
        <div style="border: #007AFF 2.5px solid;border-radius: 4px;width: 32px; background-color: #007AFF; margin: 10px 115px;"></div>
        <form>
          <div class="login">
            <div id="login_name_id" class="login_name">
              <input type="text" id="lg_name" name="lg_name" v-model="lg_name" style="margin-top: 30px;margin-bottom: 10px;width: 340px;height: 24px;font-size: 14px;"
                placeholder="请输入手机号码"></input>
            </div>
            <div id="name_msg" style="margin-right: -180px;color: #ff3366;border-bottom: #FFFFFF;" v-if="name_msg">{{n_msg}}</div>
            <div id="login_pd_id" class="login_pd">
              <input type="password" id="lg_password" name="lg_password" v-model="lg_password" style="width:340px;height: 24px;font-size: 14px;margin-top: 50px;"
                placeholder="请输入密码"></input>
            </div>
            <div id="pd_msg" style="margin-right: -180px;color: #ff3366;border-bottom: #FFFFFF" v-if="pd_msg">{{p_msg}}</div>
            <!-- <hr style="width: 362px;margin-left: -15px;" /> -->
          </div>
          <div class="login_b" id="login_b"><input type="button" value="登录" @click="login_func()"></input></div>
        </form>
      </div>
    </div>

    <h3 id="product">相关产品</h3>
    <div class="footer">
      <div class="footer_a">
        <img src="https://prox.schoolpal.cn/common/images/icon-scp.png"></img>
        <div class="footer_a_serc">
          <div style="font-weight: bold;font-size: 14px;">校园收银宝</div>
          <div style="font-size: 12px;">学校收费标准</div>
        </div>
      </div>
      <div class="footer_a">
        <img src="https://prox.schoolpal.cn/common/images/icon-zhaoshengbao.png"></img>
        <div class="footer_a_serc">
          <div style="font-weight: bold;font-size: 14px;">校园招生宝</div>
          <div style="font-size: 12px;">一站招生服务</div>
        </div>
      </div>
      <div class="footer_a">
        <img src="https://prox.schoolpal.cn/common/images/icon-anxinbao.png"></img>
        <div class="footer_a_serc">
          <div style="font-weight: bold;font-size: 14px;">校园安心宝</div>
          <div style="font-size: 12px;">教育保险精选</div>
        </div>
      </div>
      <h3 id="consult">咨询热线</h3>
      <div class="footer_b">
        <div style="font-size: 28px;font-weight: bold;">400-6999-707</div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'Login',
    data() {
      return {
        lg_name: "",
        lg_password: "",
        n_msg: "",
        p_msg: "",
        name_msg: false,
        pd_msg: false,
      }
    },
    methods: {
      login_func() {
        if (this.lg_name == "" && this.lg_password == "") {
          this.name_msg = true;
          this.pd_msg = true;
          this.n_msg = "请输入手机号";
          login_name_id.style.borderBottom = "1px solid #ff3366";
          this.p_msg = "请输入密码";

          login_pd_id.style.borderBottom = "1px solid #ff3366";
        } else if (this.lg_name != "" && this.lg_password == "") {
          this.pd_msg = true;
          this.p_msg = "请输入密码";
          login_name_id.style.borderBottom = "1px solid gainsboro";
          login_pd_id.style.borderBottom = "1px solid #ff3366";
        } else if (this.lg_name == "" && this.lg_password != "") {
          this.name_msg = true;
          this.n_msg = "请输入手机号";
          login_pd_id.style.borderBottom = "1px solid gainsboro";
          login_name_id.style.borderBottom = "1px solid #ff3366";
        } else if (this.lg_name != "" && this.lg_password != "") {
          this.name_msg = false;
          this.pd_msg = false;
          var pattern = /^1[34578]\d{9}$/;
          if (pattern.test(this.lg_name)) {
            console.log("手机号码正确");
            login_name_id.style.borderBottom = "1px solid gainsboro";
          } else {
            this.name_msg = true;
            this.n_msg = "请输入正确的手机号";
            login_name_id.style.borderBottom = "1px solid #ff3366";
            console.log("手机号码错误");
          }
        }
      }
    },
  }
</script>

<style>
  .body_content {
    text-align: center;
    background-color: #F2F6FC;
    height: 100%;
    width: 100%;
    margin: 0px;
    padding: 0px;
  }

  .flexBox {
    display: flex;
    justify-content: space-between;
    font-size: 16px;
    height: 60px;
    width: 1000px;
    margin-left: 260px;
    /* text-align: center; */
    /* align-items: center; */
  }

  .left_one {
    display: flex;
    justify-content: center;
  }

  .logo-right {
    margin: auto;
    margin-right: 2px;
    display: flex;
    flex-direction: row-reverse;
  }

  .logo-right .logo-right-chid {
    margin: auto;
    width: 80px;
    text-align: center;
  }

  .logo-right .logo-right-chid:hover {
    border-bottom: 4px solid #007AFF;
  }

  .context {
    display: flex;
    justify-content: space-between;
    margin-top: 60px;

    margin: 80px 0px auto;
    margin-left: 260px;
    width: 1000px;
  }

  .context img {
    width: 560px;
    border-top-left-radius: 8px;
    border-bottom-left-radius: 8px;
  }

  .context-right {
    border-top-right-radius: 8px;
    border-bottom-right-radius: 8px;
    background-color: white;
  }

  #ph {
    margin-top: 50px;
    margin-left: 70px;
    width: 120px;
    font-size: 18px;
    font-weight: bold;
  }

  #zh {
    margin-top: 50px;
    width: 250px;
    font-size: 18px;
    font-weight: bold;
  }

  .login {
    margin-top: 70px;
    /* text-align: center; */
    margin-left: 50px;
  }

  .login input {
    border: none;
    outline: none;
    margin-left: 30px;
  }


  .context .login_b {
    margin-top: 70px;
    margin-left: 10px;
  }

  .context .login_b input {
    width: 320px;
    height: 54px;
    background-color: #007aff;
    font-size: 16px;
    border-radius: 32px;
    color: white;
    border: none;
    outline: none;
  }

  .context .login_b input:hover {
    background-color: #0064dc;
  }

  .footer {
    display: flex;
    justify-content: flex-start;
    margin-left: 260px;
  }

  .footer_a {
    border-radius: 8px;
    transition: 0.4s;
    display: flex;
    justify-content: flex-start;
    height: 60px;
    width: 210px;
    margin-right: 10px;
  }

  .footer_a:hover {
    background-color: #eaedf2;
    transform: translateY(-3px);
  }

  .footer_a img {
    height: 45px;
    width: 45px;
    margin-right: 5px;
    margin-top: 5px;
    margin-left: 30px;

  }


  .footer_a_serc {
    margin-top: 10px;
  }

  .footer_b {
    /* margin: auto; */
    margin-right: 10px;
    margin-top: 10px;
    margin-left: 55px;
    text-align: center;
  }

  #consult {
    position: relative;
    left: 135px;
    top: -60px;
  }

  #product {
    margin-top: 10px;
    margin-left: -58vw;
    /* margin-left: 260px; */
  }

  .login_name {
    width: 350px;
    border-bottom: 1px solid gainsboro;
  }

  .login_pd {
    width: 350px;
    /* padding-bottom: 10px; */
    border-bottom: 1px solid gainsboro;
  }
</style>
