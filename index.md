---
title: "辩论赛静态页面"
---

# 辩论赛

下面是一个示例，展示如何从 8:00 开始计算 15 分钟的倒计时。  
如果你在 8:00 之前打开，会显示“倒计时尚未开始”；如果在 8:00 至 8:15 之间打开，会动态显示剩余时间；如果超过 8:15，则显示“时间到”。

---

## 辩题

> 本场辩题：**科技的发展是否会让人类的情感更加疏远？**  
> （示例辩题，可根据需要自行修改）

---

## 席位分配

<table>
  <tr>
    <th>席位</th>
    <th>辩手</th>
  </tr>
  <tr>
    <td>正方一辩</td>
    <td>张三</td>
  </tr>
  <tr>
    <td>正方二辩</td>
    <td>李四</td>
  </tr>
  <tr>
    <td>反方一辩</td>
    <td>王五</td>
  </tr>
  <tr>
    <td>反方二辩</td>
    <td>赵六</td>
  </tr>
</table>

---

## 倒计时

<div id="countdown" style="font-size: 24px; font-weight: bold; margin-top: 20px;">检测时间...</div>

<script>
// 固定的开始和结束时间（本地时间）
var startTime = new Date();   // 开始时间：8:00
startTime.setHours(8, 0, 0, 0);

var endTime = new Date();     // 结束时间：8:15
endTime.setHours(8, 15, 0, 0);

// 每秒刷新倒计时
var timer = setInterval(updateCountdown, 1000);

function updateCountdown() {
  var now = new Date();
  
  // 情况1：现在时间还不到8:00
  if (now < startTime) {
    document.getElementById('countdown').innerHTML = "倒计时尚未开始";
  
  // 情况2：现在时间在8:00和8:15之间，显示剩余时间
  } else if (now >= startTime && now < endTime) {
    // 剩余秒数
    var remainingSecs = Math.floor((endTime - now) / 1000);
    var minutes = Math.floor(remainingSecs / 60);
    var seconds = remainingSecs % 60;

    // 格式化显示
    seconds = seconds < 10 ? '0' + seconds : seconds;
    document.getElementById('countdown').innerHTML = minutes + ":" + seconds;

  // 情况3：超过8:15，倒计时结束
  } else {
    clearInterval(timer);
    document.getElementById('countdown').innerHTML = "时间到！";
  }
}
</script>
