<template>
  <footer class="footer">
    <div class="container">
      <div class="row footer-top">
        <div class="col-sm-5 col-lg-5">
          <p class="padding-top-xsm">{{ description }}</p>
          <div class="text-md">
            <a v-for="item of contacts"
              :key="item.title"
              v-title="item.title"
              :href="item.link"
              :style="contactStyle"
            >
              <i :class="`fa fa-${item.icon}`"></i>
            </a>
          </div>
          <br>
          <span v-html="designer"></span>
        </div>

        <div class="col-sm-6 col-lg-6 col-lg-offset-1">
          <div class="row">
            <div class="col-sm-4">
              <h4>{{ sponsor.title }}</h4>
              <ul class="list-unstyled">
                <li v-for="item of sponsor.list" :key="item.title">
                  <a :href="item.link" target="_blank">
                    <img
                      :src="item.logo"
                      v-title="item.title"
                      :alt="item.title"
                      class="footer-sponsor-link"
                      width="98"
                    >
                  </a>
                </li>
              </ul>
            </div>

            <div class="col-sm-4">
              <h4>{{ statistics.title }}</h4>
              <ul class="list-unstyled">
                <li v-for="item of statistics.list" :key="item.title">
                  {{ item.title }}: {{ item.description }}
                </li>
              </ul>
            </div>

            <div class="col-sm-4">
              <h4>{{ other.title }}</h4>
              <ul class="list-unstyled">
                <li v-for="item of other.list" :key="item.title">
                  <a :href="item.link"
                    v-title="item.title"
                    target="_blank"
                  >
                    <i :class="`fa fa-${item.icon}`"></i>
                    {{ item.title }}
                  </a>
                </li>
              </ul>
            </div>
          </div>
        </div>
      </div>
    </div>
  </footer>
</template>

<script>
import ucloud_logo from '@/assets/images/ucloud.png';
import sendCloud_logo from '@/assets/images/sendCloud.png';
import qiniu_logo from '@/assets/images/qiniu.png';
import title from '@/directives/title';

export default {
  name: 'TheFooter',
  // 注册局部指令
  directives: {
    title
  },
  data () {
    return {
      description: 'VuejsCaff 是一个 Vuejs 的知识社区',
      contacts: [
        {
          icon: 'envelope',
          title: '反馈问题',
          link: 'mailto:342766475@qq.com'
        },
        {
          icon: 'weibo',
          title: '站长微博',
          link: 'https://weibo.com/1952075311/profile?rightmod=1&wvr=6&mod=personinfo'
        },
        {
          icon: 'weixin',
          title: '我的微信',
          link: ''
        }
      ],
      contactStyle: {
        paddingRight: '8px'
      },
      designer: `
        <span style="font-size:0.9em">Designed by
          <span style="color: #e27575;font-size: 14px;">❤</span>
          <a href="#" target="_blank" style="color:inherit">Junting</a>
        </span>
      `,
      sponsor: {
        title: '赞助商',
        list: [
          {
            logo: ucloud_logo,
            title: '本站服务器由 UCloud 赞助',
            link: 'http://www.ucloud.cn/?utm_source=zanzhu&utm_campaign=phphub&utm_medium=display&utm_content=yejiao&ytag=phphubyejiao'
          },
          {
            logo: qiniu_logo,
            title: '本站 CDN 服务由七牛赞助',
            link: 'http://www.qiniu.com/?utm_source=phphub'
          },
          {
            logo: 'https://lccdn.phphub.org/uploads/banners/XPtLlZmIN1cQbLuDFEON.png',
            title: 'Composer 镜像赞助商',
            link: 'https://www.upyun.com/'
          },
          {
            logo: sendCloud_logo,
            title: '订阅邮件赞助商：SendCloud',
            link: 'http://www.sendcloud.net/'
          }
        ]
      },
      statistics: {
        title: '统计信息',
        list: [
          {
            title: '社区会员',
            description: '22889'
          },
          {
            title: '话题数',
            description: '7397'
          },
          {
            title: '评论数',
            description: '39375'
          }
        ]
      },
      other: {
        title: '其他信息',
        list: [
          {
            icon: 'thumbs-up',
            title: '软件外包服务',
            link: 'https://vuejscaff.com/contact'
          },
          {
            icon: 'globe',
            title: '推荐网站',
            link: 'https://vuejscaff.com/sites'
          }
        ]
      }
    }
  }
}
</script>

<style scoped>
a:hover, a:focus { color: #4fc08d; transition: color .15s; }
</style>
