<template>
  <div id="app">
    <!--头部header板块-->
    <div
      :style="'background-image:url(' + sitemeta.site_header_img + ');'"
      class="header-tu">
      <div class="container">
        <div class="header-yonghu poi-container">
          <nav class="ghost-topbar">
            <ul class="menu">
              <li class="ghost-topbar-item is-icon-text"><a href="" title="测试" target="_self">
                <i
                  style="font-size: 1.2em;"
                  class="fas fa-2x poi-icon"></i>
                <span>测试</span></a>
              </li>
              <li class="ghost-topbar-item is-icon-text"><a href="" title="测试" target="_self">
                <i
                  style="font-size: 1.2em;"
                  class="fas fa-2x poi-icon"></i>
                <span>测试</span></a>
              </li>
              <li class="ghost-topbar-item is-icon-text"><a href="" title="测试" target="_self">
                <i
                  style="font-size: 1.2em;"
                  class="fas fa-2x poi-icon"></i>
                <span>测试</span></a>
              </li>
              <li class="ghost-topbar-item is-icon-text"><a href="" title="测试" target="_self">
                <i
                  style="font-size: 1.2em;"
                  class="fas fa-2x poi-icon"></i>
                <span>测试</span></a>
              </li>
            </ul>
          </nav>
        </div>
        <!-- Logo -->
        <div class="ghost-head-nav">
          <router-link class="logo nav-col" to="/" title="">
            <img
              class="ghost-logo"
              :src="sitemeta.site_logo"
              alt="梦灵神社">
          </router-link>
        </div>
      </div>
    </div>

    <!--菜单板块-->
    <div class="scroll-header-menu container"><!-- 菜单 -->
      <header class="scroll-header header-menu">
        <div style="margin:0px auto" class="header white">
          <div class="ghost-header-logo">
            <div
              :style="'background-image:url(' + sitemeta.site_header_img + ');'"
              class="header-bg">
            </div>
          </div>
          <nav class="header-nav navigation clearfix" role="navigation">

            <div class="header-menu-div">
              <ul class="ghost_menu_ul">
                <li>
                  <router-link to="/" style="padding: 10px 15px 10px 10px;font-size: 25px;"><i
                    class="catacg-mune-tubiao fas fa-home"> </i></router-link>
                </li>
                <li
                  v-for="(k, v) in menu"
                  :key="v"
                  class="menu-item menu-item-type-taxonomy menu-item-object-category menu-item-has-children menu-item-26519">
                  <router-link :to="'/category/'+(k.value)">
                    <i :class="'catacg-mune-tubiao '+(k.icon)"> </i>{{ k.label }}
                    <i class="ghost-menu-posts-count" title="本周发布的">{{ k.num }}</i>
                  </router-link>
                  <ul class="sub-menu">
                    <li
                      v-for="(k, v) in k.children"
                      :key="v"
                      class="menu-item menu-item-type-taxonomy menu-item-object-category menu-item-26520">
                      <router-link :to="'/category/'+(k.value)">
                        <i :class="'catacg-mune-tubiao '+(k.icon)"> </i>{{ k.label }}
                      </router-link>
                    </li>
                  </ul>
                </li>
              </ul>
            </div>
            <div class="ghost-nav-tool__container">
              <div v-if="login" class="ghost_sign_daily">
                <a style="background: #ff83c466" class="ghost_sign_daily_btn" title="已签到">
                  <span class="poi-icon fa-map-marker fas fa-fw" aria-hidden="true"></span>
                  <span class="poi-icon__text">已签到</span>
                </a>
              </div>
              <li v-if="!login" @click="sign=true" class="login-actions">
                <a class="user-login login-link bind-redirect"><span>登陆</span></a>
              </li>
              <li v-if="login" class="login-actions">
                <i
                  class="ghost-author-posts-count"
                  title="未读消息数量"
                  style="background: red;border-radius: 50%;right: 48px;top: 5px;padding: 5px;"></i>
                <a
                  style="padding:0px;background: hsla(0, 0%, 100%, 0);"
                  class="login-link bind-redirect">
                  <img
                    src="https://img.catacg.cn/pinkacg_upload/img/2020/06/6027905533d2eec5809d812f5cd69d14f04263f0.png"
                    alt=""
                    class="ghost_guajian">
                  <img
                    src=""
                    alt="avatar"
                    class="ghost_setting_content_avatar_img"
                    width="100"
                    height="100">
                </a>

                <div class="ghost_user_menu_nav">
                  <div class="ghost_user_menu_item">
                    <div class="ghost_user_menu_item_title">
                      <div class="ghost_user_menu_item_title_icon">
                        <i class="poi-icon fas fa-address-card" aria-hidden="true"></i>
                      </div>
                      <div class="ghost_user_menu_item_title_text">个人设置</div>
                    </div>
                    <router-link
                      to="/user/setting"
                      title="我的设置"
                      class="ghost_user_menu_item_link">
                      <div class="ghost_user_menu_item_link_icon">
                        <i class="poi-icon fas fa-cog" aria-hidden="true"></i>
                      </div>
                      <div class="ghost_user_menu_item_link_text">我的设置</div>
                    </router-link>
                    <router-link
                      to="/user/drafts"
                      title="我的文章"
                      class="ghost_user_menu_item_link">
                      <div class="ghost_user_menu_item_link_icon">
                        <i class="poi-icon fas fa-copy" aria-hidden="true"></i>
                      </div>
                      <div class="ghost_user_menu_item_link_text">我的草稿</div>
                    </router-link>
                    <router-link
                      to="/user/newpost"
                      title="新建文章"
                      class="ghost_user_menu_item_link">
                      <div class="ghost_user_menu_item_link_icon">
                        <i class="poi-icon fas fa-paint-brush" aria-hidden="true"></i>
                      </div>
                      <div class="ghost_user_menu_item_link_text">新建文章</div>
                    </router-link>
                  </div>
                  <div class="ghost_user_menu_item">
                    <div class="ghost_user_menu_item_title">
                      <div class="ghost_user_menu_item_title_icon">
                        <i class="poi-icon fa-bell fas" aria-hidden="true"></i>
                      </div>
                      <div class="ghost_user_menu_item_title_text">消息管理</div>
                    </div>
                    <i
                      style="top: 64px;right: 82px;"
                      class="ghost-author-posts-count"
                      title="未读通知数量">1</i>
                    <router-link
                      to="/user/notice"
                      title="我的通知"
                      class="ghost_user_menu_item_link">
                      <div class="ghost_user_menu_item_link_icon">
                        <i class="poi-icon fas fa-bell" aria-hidden="true"></i>
                      </div>
                      <div class="ghost_user_menu_item_link_text">我的通知</div>
                    </router-link>
                    <router-link
                      to="/user/msg"
                      title="我的消息"
                      class="ghost_user_menu_item_link">
                      <div class="ghost_user_menu_item_link_icon">
                        <i class="poi-icon fas fa-envelope" aria-hidden="true"></i>
                      </div>
                      <div class="ghost_user_menu_item_link_text">我的消息</div>
                    </router-link>
                    <router-link
                      to="/user/orders"
                      title="我的订单"
                      class="ghost_user_menu_item_link">
                      <div class="ghost_user_menu_item_link_icon">
                        <i class="poi-icon fas fa-shopping-cart" aria-hidden="true"></i>
                      </div>
                      <div class="ghost_user_menu_item_link_text">我的订单</div>
                    </router-link>
                  </div>
                  <div class="ghost_user_menu_item">
                    <div class="ghost_user_menu_item_title">
                      <div class="ghost_user_menu_item_title_icon">
                        <i class="poi-icon fas fa-user-circle" aria-hidden="true"></i>
                      </div>
                      <div class="ghost_user_menu_item_title_text">个人中心</div>
                    </div>
                    <router-link
                      to="/user/stars"
                      title="我的收藏"
                      class="ghost_user_menu_item_link">
                      <div class="ghost_user_menu_item_link_icon">
                        <i class="poi-icon fas fa-heart" aria-hidden="true"></i>
                      </div>
                      <div class="ghost_user_menu_item_link_text">我的收藏</div>
                    </router-link>
                    <router-link
                      to="/user/posts"
                      title="我的文章"
                      class="ghost_user_menu_item_link">
                      <div class="ghost_user_menu_item_link_icon">
                        <i class="poi-icon fas fa-file-alt" aria-hidden="true"></i>
                      </div>
                      <div class="ghost_user_menu_item_link_text">我的文章</div>
                    </router-link>
                    <router-link
                      to="/user/fans"
                      title="我的粉丝"
                      class="ghost_user_menu_item_link">
                      <div class="ghost_user_menu_item_link_icon">
                        <i class="poi-icon fa-users fas" aria-hidden="true"></i>
                      </div>
                      <div class="ghost_user_menu_item_link_text">我的粉丝</div>
                    </router-link>
                  </div>
                  <div class="ghost_user_menu_item">
                    <div class="ghost_user_menu_item_title">
                      <div class="ghost_user_menu_item_title_icon">
                        <i class="poi-icon fas fa-user-circle" aria-hidden="true"></i>
                      </div>
                      <div class="ghost_user_menu_item_title_text">我的会员</div>
                    </div>
                    <router-link
                      to="/user/vip"
                      title="我的会员"
                      class="ghost_user_menu_item_link">
                      <div class="ghost_user_menu_item_link_icon">
                        <i class="poi-icon fas fa-user-circle" aria-hidden="true"></i>
                      </div>
                      <div class="ghost_user_menu_item_link_text">我的会员</div>
                    </router-link>
                    <router-link
                      to="/user/cash"
                      title="我的余额"
                      class="ghost_user_menu_item_link">
                      <div class="ghost_user_menu_item_link_icon">
                        <i class="poi-icon fas fa-credit-card" aria-hidden="true"></i>
                      </div>
                      <div class="ghost_user_menu_item_link_text">我的余额</div>
                    </router-link>
                    <router-link
                      to="/user/credits"
                      title="我的积分"
                      class="ghost_user_menu_item_link">
                      <div class="ghost_user_menu_item_link_icon">
                        <i class="poi-icon fas fa-gem" aria-hidden="true"></i>
                      </div>
                      <div class="ghost_user_menu_item_link_text">我的积分</div>
                    </router-link>
                  </div>
                  <div class="ghost_user_menu_item">
                    <div class="ghost_user_menu_item_title">
                      <div class="ghost_user_menu_item_title_icon">
                        <i class="poi-icon fas fa-unlock" aria-hidden="true"></i>
                      </div>
                      <div class="ghost_user_menu_item_title_text">管理设置</div>
                    </div>
                    <router-link
                      to="/user/shop"
                      title="商城中心"
                      class="ghost_user_menu_item_link">
                      <div class="ghost_user_menu_item_link_icon">
                        <i class="poi-icon fas fa-gem" aria-hidden="true"></i>
                      </div>
                      <div class="ghost_user_menu_item_link_text">商城中心</div>
                    </router-link>
                    <router-link
                      to="/user/price"
                      title="积分抽奖"
                      class="ghost_user_menu_item_link">
                      <div class="ghost_user_menu_item_link_icon">
                        <i class="poi-icon fas fa-gem" aria-hidden="true"></i>
                      </div>
                      <div class="ghost_user_menu_item_link_text">积分抽奖</div>
                    </router-link>
                    <router-link
                      to="/user/logout"
                      title="注销账号"
                      class="ghost_user_menu_item_link">
                      <div class="ghost_user_menu_item_link_icon">
                        <i class="poi-icon fas fa-sign-out-alt" aria-hidden="true"></i>
                      </div>
                      <div class="ghost_user_menu_item_link_text">注销账号</div>
                    </router-link>
                  </div>
                </div>

              </li>
              <div class="ghost_header_search_anniu ghost-search-bar_toggle-btn_container">
                <a
                  @click="search=true"
                  class="poi-icon fa-search fa fa-2x ghost-search-bar_btn"
                  aria-label="搜索"
                  title="搜索"></a>
              </div>
            </div>
          </nav>
        </div>
      </header>
    </div>

    <!--主要内容板块-->
    <router-view :key="key" />

    <!--footer板块-->
    <footer class="footer">
      <div class="footer-wrap">
        <!-- 页脚菜单/版权信息 IDC No. -->
        <div class="footer-nav">
          <div class="ghost-footer-width">
            <div class="ghost-footer">
              <aside>
                <div class="widget widget_text">
                  <div class="heading">
                    <i class="fas fa-link"></i><span class="widget-title">链接导航</span>
                  </div>
                  <div class="textwidget">
                    <ul class="ghost-links-daohang">
                      <li class="ghost-footer-link"><a class="ghost-footer-links" href="https://otakusns.com/">御宅社</a>
                      </li>
                      <li class="ghost-footer-link"><a class="ghost-footer-links" href="https://mkw2023.com/">梦灵神社</a>
                      </li>
                      <li class="ghost-footer-link"><a class="ghost-footer-links" href="https://PILIACG.CN">piliacg/霹雳acg</a>
                      </li>
                      <li class="ghost-footer-link"><a class="ghost-footer-links" href="https://19moe.com/">妖九萌</a>
                      </li>
                      <li class="ghost-footer-link"><a class="ghost-footer-links" href="https://www.onlolikon.com/">音域动漫|分享动漫资源</a>
                      </li>
                      <li class="ghost-footer-link"><a
                        class="ghost-footer-links"
                        href="https://miaokadm.com/">喵咔动漫</a>
                      </li>
                      <li class="ghost-footer-link"><a class="ghost-footer-links" href="https://www.dibidibi.cn/">嘀哔嘀哔（dibidibi）</a>
                      </li>
                      <li class="ghost-footer-link"><a
                        class="ghost-footer-links"
                        href="http://www.moe321.com/">萌站·次元导航</a></li>
                      <li class="ghost-footer-link"><a
                        class="ghost-footer-links"
                        href="http://www.huo2.cn/">火二次元导航</a>
                      </li>
                      <li class="ghost-footer-link"><a
                        class="ghost-footer-links"
                        href="http://www.jspoo.com">聚神铺导航</a>
                      </li>
                      <li class="ghost-footer-link"><a
                        class="ghost-footer-links"
                        href="https://www.loveu8.cn/">幻梦博客</a>
                      </li>
                      <li class="ghost-footer-link"><a
                        class="ghost-footer-links"
                        href="https://logirlsns.com/">萌娘社区</a>
                      </li>
                      <li class="ghost-footer-link"><a class="ghost-footer-links" href="https://moe.ac/">萌点动漫</a></li>
                      <li class="ghost-footer-link"><a class="ghost-footer-links" href="https://zuiacg.moe/">最ACG</a>
                      </li>
                      <li class="ghost-footer-link"><a class="ghost-footer-links" href="https://acghf.com/">ACG汉服社</a>
                      </li>
                      <li class="ghost-footer-link"><a
                        class="ghost-footer-links"
                        href="https://acgmv.srsg.moe/">绯萌社区</a></li>
                      <li class="ghost-footer-link"><a
                        class="ghost-footer-links"
                        href="https://www.ecy1.net/">次元一区</a>
                      </li>
                      <li class="ghost-footer-link"><a class="ghost-footer-links" href="https://aibenzi.com/">最ACG</a>
                      </li>
                      <li class="ghost-footer-link"><a
                        class="ghost-footer-links"
                        href="https://www.c3acg.com/">C3动漫</a>
                      </li>
                      <li class="ghost-footer-link"><a class="ghost-footer-links" href="https://cangku.one/">绅士仓库</a>
                      </li>
                      <li class="ghost-footer-link"><a class="ghost-footer-links" href="http://www.pmjun.com/">泡面菌</a>
                      </li>
                      <li class="ghost-footer-link"><a class="ghost-footer-links" href="http://www.haitangw.cn">海棠网-专注ACG动漫资讯,新番动漫,二次元</a>
                      </li>
                      <li class="ghost-footer-link"><a class="ghost-footer-links" href="https://moegirl.xyz">萌娘导航</a>
                      </li>
                    </ul>
                  </div>
                </div>
              </aside>
            </div>
            <div class="ghost-footer">
              <aside>
                <div class="widget widget_text">
                  <div class="heading">
                    <i class="fas fa-bullhorn"></i><span class="widget-title">声明</span>
                  </div>
                  <div class="textwidget">
                    申明：本站属于互联网自由分享，所有bt文件均来自互联网，分享于互联网，本站只作为一个bt暂存平台；本站并不属于bt的提供者、制作者、所有者，因此本站不承担任何法律责任!
                  </div>
                </div>
              </aside>
            </div>
            <div class="ghost-footer">
              <aside>
                <div class="widget widget_text">
                  <div class="heading">
                    <i class="fas fa-user-circle"></i><span class="widget-title">关于我们</span>
                  </div>
                  <div class="textwidget">梦灵神社-ACG一站式分享平台，包含 动漫资讯、漫展信息、动漫美图、动漫周边，动漫音乐等跟二次元相关内容，欢迎投稿</div>
                </div>
              </aside>
            </div>
            <div class="ghost-footer">
              <aside>
                <div class="widget widget_text">
                  <div class="heading">
                    <i class="fas fa-envelope"></i><span class="widget-title">联系我们</span>
                  </div>
                  <div class="textwidget"><p>新浪微博：暂无</p>
                    <p>腾讯 QQ：2877136577</p>
                    <p>q群：<a href="暂无">暂无</a>
                    </p>
                    <p><a href="暂无">暂无</a></p></div>
                </div>
              </aside>
            </div>
          </div>
        </div>
      </div>
    </footer>

    <!--版权板块-->
    <div class="ghost_bottom_tools" style="display: block;">
      <div class="container">
        <div class="ghost_bottom_tools_container">
          <div class="ghost_bottom_tool_container">
            <div class="ghost_bottom_tools_top_item">
              <a class="ghost_bottom_tools_top_link" @click="backtop" title="返回顶部"><span
                                                                                     class="ghost_bottom_tools_top_icon poi-icon fa-arrow-up fas fa-fw"></span>
                <span class="ghost_bottom_tools_top_text">返回顶部</span>
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!--    底部版权-->
    <div class="ghost_footer">© <a href="https://pinkacg.com/">粉萌次元</a> 2020 THEME BY <a
      href="https://catacg.cn/index.php/35.html">GHOST</a></div>

    <!--    搜索蒙板-->
    <div v-show="search" class="ghost_search_bar ghost_dialog">
      <div @click="search=!search" class="ghost_search_bar_ ghost_dialog_ open"></div>
      <div class="search_bar ghost_search_box_container open">
        <div>
          <form method="get" role="search" class="search_bar_form">
            <label class="search_bar_label">搜索</label>
            <input type="search" name="s" class="search_bar_input" placeholder="试试：漫画" aria-label="搜索">
          </form>
          <div class="search_bar_all"><a class="search_bar_item">动漫</a><a class="search_bar_item">小说</a><a class="search_bar_item">漫画</a></div>
        </div>
      </div>
    </div>

    <!--    登陆蒙板-->
    <div v-show="sign" class="ghost_login_bar ghost_dialog">
      <div @click="sign=!sign" class="ghost_login_bar_ ghost_dialog_ open"></div>
      <div class="ghost_login_box ghost_dialog_box">
        <div class="ghost_login_box_container open">
          <form
            ref="loginForm"
            :model="user"
            :rules="rules"
            action="javascript:;"
            id="ghost_login_box_form"
            class="ghost_login_box_form">
            <header class="ghost_login_box_header">
              <div class="ghost_login_box_title">
                <div class="ghost_login_box_title_left">
                  <a @click="loginmod=true,regmod=false,forgetmod=false" :class="loginmod ? ' is-active' : ''" class="login ghost_login_box_title_left_item">登录</a>
                  <a @click="regmod=true,loginmod=false,forgetmod=false" :class="regmod ? ' is-active' : ''" class="reg ghost_login_box_title_left_item">注册</a>
                  <a @click="forgetmod=true,regmod=false,loginmod=false" :class="forgetmod ? ' is-active' : ''" class="forget ghost_login_box_title_left_item">丢失密码</a></div>
                <a @click="sign=!sign" class="ghost_login_box_close">
                  <span class="poi-icon fa-times fas fa-fw" aria-hidden="true"></span>
                </a>
              </div>
            </header>
            <div class="ghost_login_box_content">
              <div class="ghost_login_box_content_text">
                <div>
                  <div><p>欢迎登录粉萌次元！</p></div>
                  <div v-if="loginmod" class="content">
                    <div class="ghost_login_box_content_group">
                      <label class="login_input ghost_login_box_content_inputs" style="margin: 0px 10px;">
                        <span class="ghost_login_box_content_inputs_icon">
                          <span class="poi-icon fa-user fas fa-fw" aria-hidden="true"></span>
                        </span>
                        <span class="poi-form__group__inputs__content">
                          <input
                            v-model="user.username"
                            type="email"
                            class="ghost_login_box_content_input user"
                            placeholder="您的电子邮件"
                            title="您的电子邮件"
                            required=""
                            tabindex="1"
                            minlength="5"
                            value=""></span>
                      </label>
                    </div>
                    <div class="ghost_login_box_content_group">
                      <label class="login_input ghost_login_box_content_inputs" style="margin: 0px 10px;">
                        <span class="ghost_login_box_content_inputs_icon">
                          <span class="poi-icon fa-unlock-alt fas fa-fw" aria-hidden="true"></span>
                        </span>
                        <span class="poi-form__group__inputs__content">
                          <input
                            v-model="user.password"
                            type="password"
                            class="ghost_login_box_content_input pwd"
                            placeholder="密码"
                            title="密码"
                            required=""
                            tabindex="1"
                            value=""></span>
                      </label>
                    </div>
                    <div class="ghost_login_box_content_group">
                      <label class="login_input_ ghost_login_box_content_inputs" style="margin: 0px 10px;">
                        <span class="ghost_login_box_content_inputs_icon">
                          <span class="poi-icon fa-unlock-alt fas fa-fw" aria-hidden="true"></span>
                        </span>
                        <span class="poi-form__group__inputs__content">
                          <input
                            v-model="user.captcha"
                            type="captcha"
                            class="ghost_login_box_content_input pwd"
                            placeholder="验证码"
                            title="验证码"
                            required=""
                            tabindex="1"
                            value="">
                        </span>
                      </label>
                      <label class="login_input_ ghost_login_box_content_inputs" style="margin: 0px 10px;">
                        <div v-if="captchaImg">
                          <img style="height: 40px;" :src="captchaImg" @click="restfulCaptcha" alt="验证码">
                        </div>
                      </label>
                    </div>
                    <div v-if="false" class="ghost_login_box_content_group">
                      <label class="remembermetext" for="rememberme"><input type="checkbox" checked="checked" id="rememberme" class="rememberme" value="forever">14天内记住登录</label>
                    </div>
                  </div>
                  <div v-if="regmod" class="content">
                    <div class="is-register">
                      <div class="ghost_login_box_content_group clearfix">
                        <label style="margin:0px 10px;" class="ghost_login_box_content_inputs">
                          <span class="ghost_login_box_content_inputs_icon">
                            <span class="poi-icon fa-at fas fa-fw" aria-hidden="true"></span>
                          </span>
                          <span class="poi-form__group__inputs__content">
                            <input
                              type="email"
                              name="email"
                              class="ghost_login_box_content_input email"
                              placeholder="您的电子邮箱"
                              title="您的电子邮箱"
                              required=""
                              tabindex="1"
                              minlength="5"
                              value="">
                          </span>
                        </label>
                      </div>
                      <div class="ghost_login_box_content_group clearfix">
                        <label class="login_input_ ghost_login_box_content_inputs">
                          <span class="ghost_login_box_content_inputs_icon">
                            <span class="poi-icon fa-pencil-alt fas fa-fw" aria-hidden="true">
                            </span>
                          </span>
                          <span class="poi-form__group__inputs__content">
                            <input
                              name="veriCode"
                              type="veriCode"
                              class="ghost_login_box_content_input veriCode"
                              placeholder="邮箱验证码"
                              title="邮箱验证码"
                              required=""
                              tabindex="1"
                              value="">
                          </span>
                        </label>
                        <label class="login_veriCode_login_input">
                          <a data-type="getforgetcode" class="login_veriCode">
                            <span class="poi-icon fa-paper-plane fas fa-fw" aria-hidden="true">
                            </span>
                            <span class="ghost_icon_text">发送验证码</span>
                          </a>
                        </label>
                      </div>
                      <div class="ghost_login_box_content_group clearfix">
                        <label style="margin:0px 10px;" class="ghost_login_box_content_inputs">
                          <span class="ghost_login_box_content_inputs_icon">
                            <span class="poi-icon fa-lock fas fa-fw" aria-hidden="true">
                            </span>
                          </span>
                          <span class="poi-form__group__inputs__content">
                            <input
                              type="pwd"
                              name="password"
                              class="ghost_login_box_content_input pwd"
                              placeholder="您的新密码"
                              title="您的新密码"
                              required=""
                              tabindex="1"
                              minlength="5"
                              value="">
                          </span>
                        </label>
                      </div>
                    </div>
                  </div>
                  <div v-if="forgetmod" class="content">
                    <div class="is-register">
                      <div class="ghost_login_box_content_group clearfix">
                        <label style="margin:0px 10px;" class="ghost_login_box_content_inputs">
                          <span class="ghost_login_box_content_inputs_icon">
                            <span class="poi-icon fa-user fas fa-fw" aria-hidden="true">
                            </span>
                          </span>
                          <span class="poi-form__group__inputs__content">
                            <input
                              type="username"
                              name="username"
                              class="ghost_login_box_content_input username"
                              placeholder="请使用英文字符"
                              title="您的昵称"
                              required=""
                              tabindex="1"
                              minlength="5"
                              value="">
                          </span>
                        </label>
                      </div>
                      <div class="ghost_login_box_content_group clearfix">
                        <label style="margin: 0px 10px;" class="login_input ghost_login_box_content_inputs">
                          <span class="ghost_login_box_content_inputs_icon">
                            <span class="poi-icon fa-at fas fa-fw" aria-hidden="true">
                            </span>
                          </span>
                          <span class="poi-form__group__inputs__content">
                            <input
                              name="email"
                              type="username"
                              class="ghost_login_box_content_input email"
                              placeholder="您的用户名"
                              title="您的用户名"
                              required=""
                              tabindex="1"
                              value="">
                          </span>
                        </label>
                        <label style="margin: 0px 10px;" class="login_input ghost_login_box_content_inputs">
                          <span class="ghost_login_box_content_inputs_icon">
                            <span class="poi-icon fa-unlock-alt fas fa-fw" aria-hidden="true">
                            </span>
                          </span>
                          <span class="poi-form__group__inputs__content">
                            <input
                              name="pwd"
                              type="password"
                              class="ghost_login_box_content_input pwd"
                              placeholder="密码"
                              title="密码"
                              required=""
                              tabindex="1"
                              value="">
                          </span>
                        </label>
                      </div>
                      <div class="ghost_login_box_content_group clearfix">
                        <label class="login_input_ ghost_login_box_content_inputs">
                          <span class="ghost_login_box_content_inputs_icon">
                            <span class="poi-icon fa-pencil-alt fas fa-fw" aria-hidden="true">
                            </span>
                          </span>
                          <span class="poi-form__group__inputs__content">
                            <input
                              name="veriCode"
                              type="veriCode"
                              class="ghost_login_box_content_input veriCode"
                              placeholder="邮箱验证码"
                              title="邮箱验证码"
                              required=""
                              tabindex="1"
                              value="">
                          </span>
                        </label>
                        <label class="login_veriCode_login_input">
                          <a data-type="getregcode" class="login_veriCode">
                            <span class="poi-icon fa-paper-plane fas fa-fw" aria-hidden="true">
                            </span>
                            <span class="ghost_icon_text">发送验证码</span>
                          </a>
                        </label>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
            <footer class="ghost_login_box_footer">
              <button
                @click="submitUserType()"
                data-type="login"
                type="submit"
                value="undefined"
                class="ghost_login_box_footer_btn login"
                tabindex="1">
                <span class="poi-icon fa-arrow-alt-circle-right fas fa-fw" aria-hidden="true"></span>
                <span class="ghost_icon_text">登录</span></button>
            </footer>
          </form>
        </div>
      </div>
    </div>

  </div>
</template>

<script>
import { categories } from '@/api/categories'
import { sitesetting } from '@/api/sitemeta'
import { getCaptcha } from '@/api/login'

export default {
  name: 'Layout',
  data () {
    return {
      user: {
        username: '',
        password: '',
        captcha: '',
        key: ''
      },
      rules: {
        username: [{ required: true, message: '用户名不能为空', trigger: 'blur' }],
        password: [{ required: true, message: '密码不能为空', trigger: 'blur' }],
        captcha: [{ required: true, message: '验证码不能为空', trigger: 'blur' }]
      },
      login: false,
      search: false,
      sign: false,
      loginmod: true,
      regmod: false,
      forgetmod: false,
      captchaKey: '',
      captchaImg: '',
      menu: [],
      sitemeta: []
    }
  },
  created () {
    this.getCaptcha()
    this.site_setting()
    this.categories()
  },
  computed: {
    key () {
      return this.$route.name ? this.$route.name + +new Date() : this.$route + +new Date()
    }
  },
  methods: {
    restfulCaptcha () {
      this.getCaptcha()
    },
    async getCaptcha () {
      const data = await getCaptcha()
      this.captchaImg = data.img
      this.user.key = data.key
    },
    submitUserType () {
      if (this.loginmod) {
        this.$store.dispatch('user/login', this.user).then(() => {
          console.log(1212);
          this.$router.push({ path: '/' })
          this.loading = false
        }).catch(() => {
          this.loading = false
        })
      } else if (this.regmod) {

      } else if (this.forgetmod) {

      }
    },
    geturl (url) {
      return process.env.VUE_APP_API_BASE_SITE_URL + '/' + url
    },
    async categories () {
      const { data } = await categories()
      this.menu = data
    },
    async site_setting () {
      this.sitemeta = await sitesetting()
      this.sitemeta.site_logo = this.geturl(this.sitemeta.site_logo)
      this.sitemeta.site_header_img = this.geturl(this.sitemeta.site_header_img)
    },
    backtop () {
      const timer = setInterval(function () {
        const osTop = document.documentElement.scrollTop || document.body.scrollTop
        const ispeed = Math.floor(-osTop / 5)
        document.documentElement.scrollTop = document.body.scrollTop = osTop + ispeed
        this.isTop = true
        if (osTop === 0) {
          clearInterval(timer)
        }
      }, 10)
    }
  }
}
</script>

<style lang='less' scoped>
</style>
