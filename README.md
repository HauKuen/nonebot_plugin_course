<div align="center">

# nonebot-plugin-course
### ✨*基于Nonebot2的课表查询插件*✨
</div>
<div align="center">
<img src="https://img.shields.io/badge/python-3.8.10-green" alt="python"> <img src="https://img.shields.io/badge/license-MIT-blue" alt="license">
</div>

## 💡写在前面

特别感谢[hamo](https://github.com/hamo-reid)的[*nonebot_plugin_PicMenu*](https://github.com/hamo-reid/nonebot_plugin_PicMenu)提供的图片生成工具img_tool和很多思路

算是菜鸡写的第一个完整的工程项目，代码似乎十分屎山，但作为总计写python不到两个月的人来说，我还是较为有成就感的。之后有空再重构，所以有什么改进建议或者在使用时遇到bug，欢迎狠狠地提Issue

## 🔔功能
 
* 📖完整课表
* 📙本周课表
* 🧾下周课表
* 🔍查询指定周数课表
* 🕑查询当前在上什么课，今天还有没有课
* 📆支持设定周数
* 📌添加课表过程简单，与主流课表app流程无太大区别

    ### 🎯To_do

    ⬜︎ 如果今天没课了，跨天或跨周查询离现在最近的一节课还有多久（课少的时候看着很赏心悦目

    ⬜︎ 相同课的表格合并

    ⬜︎ 优化添加课程时的逻辑与繁琐度

    ⬜︎ 保姆式开箱即用

    ⬜︎ 支持不同账号设定不同的上下课时间，而非一个bot共用一套上下课时间
    <!-- ☑︎ -->

    ### 暂时不会考虑添加的功能
    - 用对话添加课表：因为一周内的课十分的多，多的时候会添加5×13次，而这都需要一次一次地在聊天框输入后发送，若遇传参问题会增加复杂度，反而本末倒置了。若是在群组里添加也会十分地刷屏。

## 💿如何使用
### 下载
#### 方法一


#### 方法二
- Step1
    ```
    pip install nonebot_plugin_course
    ```
- Step2
  在pyproject.toml里的`plugins = []`添加`"nonebot_plugin_course"`

### 初次使用
1. 上一步完成以后启动一次bot，会自动在根目录的/data文件夹(即bot.py所在文件夹)下生成一个名为course_config的文件夹
   
2. 打开里面的config.json文件，将"default"字段的值改为任意字体的路径，字体格式为[PIL.ImageFont.truetype](https://pillow.readthedocs.io/en/stable/reference/ImageFont.html?highlight=truetype#PIL.ImageFont.truetype)所支持的字体，比如将第一行改为`"default": "simhei.ttf"`

3. 保存json文件后就可以快乐地添加课表了

4. 在任意一个群内发送“完整课表”，即可初始化当前帐号的课表结构

![](https://github.com/InariInDream/nonebot_plugin_course/blob/main/resources/2022-08-22-23-33-19.png)

![](https://github.com/InariInDream/nonebot_plugin_course/blob/main/resources/2022-08-22-23-11-43.png)

1. 根据自己的课表情况填写即可

### 功能展示
![](https://github.com/InariInDream/nonebot_plugin_course/blob/main/resources/2022-08-22-23-19-00.png)

![](https://github.com/InariInDream/nonebot_plugin_course/blob/main/resources/2022-08-22-23-20-19.png)

![](https://github.com/InariInDream/nonebot_plugin_course/blob/main/resources/2022-08-22-23-22-17.png)

![](https://github.com/InariInDream/nonebot_plugin_course/blob/main/resources/2022-08-22-23-22-56.png)

![](https://github.com/InariInDream/nonebot_plugin_course/blob/main/resources/2022-08-22-23-23-40.png)

## ❗注意事项

**不同学校的上课时间有所不同**，默认设定的时间仅代表作者的学校。因此，请**务必**确认utils.py里的
```py
# 上下课时间
self.exact_time = {
    "1": {"start": "08:20", "end": "09:05"},
    "2": {"start": "09:10", "end": "09:55"},
    "3": {"start": "10:15", "end": "11:00"},
    "4": {"start": "11:05", "end": "11:50"},
    "5": {"start": "11:55", "end": "12:25"},
    "6": {"start": "12:30", "end": "13:00"},
    "7": {"start": "13:10", "end": "13:55"},
    "8": {"start": "14:00", "end": "14:45"},
    "9": {"start": "15:05", "end": "15:50"},
    "10": {"start": "15:55", "end": "16:40"},
    "11": {"start": "18:00", "end": "18:45"},
    "12": {"start": "18:50", "end": "19:35"},
    "13": {"start": "19:40", "end": "20:25"},
}
```
和template.py里的
```py
exact_time = {
    "1": {"start": "08:20", "end": "09:05"},
    "2": {"start": "09:10", "end": "09:55"},
    "3": {"start": "10:15", "end": "11:00"},
    "4": {"start": "11:05", "end": "11:50"},
    "5": {"start": "11:55", "end": "12:25"},
    "6": {"start": "12:30", "end": "13:00"},
    "7": {"start": "13:10", "end": "13:55"},
    "8": {"start": "14:00", "end": "14:45"},
    "9": {"start": "15:05", "end": "15:50"},
    "10": {"start": "15:55", "end": "16:40"},
    "11": {"start": "18:00", "end": "18:45"},
    "12": {"start": "18:50", "end": "19:35"},
    "13": {"start": "19:40", "end": "20:25"},
}
```
是否与使用者的上下课时间相符合
