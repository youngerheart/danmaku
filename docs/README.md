## 关于依赖
前端原生，后端express + 自制的node-websocket 

## 关于用法
通常来说弹幕都是跑在视频上的，但是我想做成这样的东西，它有一个配置，传入这些参数:

      const config = {
        el: xxx, // 一个dom对象，也就是弹幕的载体，需要固定的长宽
        time: 60000, // 播放时间，单位为毫秒
        url: xxx // 请求后端websocket的接口
      };
      
      const user = {}; // 用户信息
      
      const option = {
        color: #xxx, // 弹幕颜色
        size: xxpx, // 弹幕大小
        type: 'top', // 弹幕类型(top, flow, bottom)
      }

具有这些方法:

      const danmaku = new Danmaku(config, user); // 需要用到配置与用户信息
      danmaku.play(); // 播放
      danmaku.pause(); // 暂停
      danmaku.stop(); // 停止
      danmaku.input(str); // 发送弹幕
      danmaku.set('option', option); // 设置弹幕的样式

## 关于弹幕格式
可以用一个对象储存，key为时间，根据当前播放的时间点取出当前弹幕来播放。

      {
        '23:33:33 3300': [
          {
            user: ...,
            color: ...,
            size: ...,
            type: ...,
            text: ...,
            time: '2015-11-02 23:33:33 3300' // 发送弹幕时的服务器时间
          },{
            ...
          }
        ],
        ...
      }
