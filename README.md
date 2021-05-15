**提示：(项目失效，IBM最近开始封号)**

1：用的人增多，肯定会封，用起来别太狠，建议轻度用户使用

2：脚本默认情况下：定时每周四的UTC时间20:00（北京时间周五凌晨4:00）重新部署一次，大家可以根据workflows中cron自行配置Action执行

3：默认内存设置为256M，使用达拉斯地区


   | Secrets变量 | 形式 |
  | --------------------- | ----------- |
  | `IBM_CF_USERNAME`       | IBM Cloud 邮箱地址 |
  | `IBM_CF_PASSWORD` | IBM Cloud 邮箱密码 |
  | `IBM_CF_APP_NAME` | IBM Cloud 应用程序名 |
  | `V2_UUID` | 自定义UUID码 |
  | `V2_WS_PATH_VMESS` </br> `V2_WS_PATH_VLESS` | 协议选择一个，填入自定义PATH路径 |
  
注：VMESS默认的alterId为64

CloudFlare的Workers反代，请使用下列脚本：
<pre name="code" class="javascript">
addEventListener(
"fetch",event => {
let url=new URL(event.request.url);
url.hostname="ibm host address";
url.pathname = "ws pathname";
let request=new Request(url,event.request);
event. respondWith(
fetch(request)
)
}
)
</pre>

本项目基于P3TERX和ygtsj项目修改而来，感谢两位前辈.

