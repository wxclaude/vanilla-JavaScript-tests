### 初始思路：
1. 通过keydown事件监听按下的键。
>如果符合对应的data-key，则将对应data-key的div添加高亮样式playing，并且播放对应的audio

2. audio结束的时候去掉对应data-key的div的样式playing

### 遇到的难点：
1. 如何保证audio播放结束后自动去掉highlight？
>给每个div绑定transitionend事件用于监听audio播放结束

>[有关transitionend及animationend](http://www.15yan.com/story/bYNqBSgbGKv/)

>在移除对应类的时候，需要判断下是不是变化的是transform属性，

>highlight类里变化的是transform，只有在这个时候才去除highlight，顺便复习下[event属性](http://www.cnblogs.com/coolicer/archive/2010/10/04/1842653.html)

2. 如果一直按着键，如何保证连续响声？
>其实就是不停的触发audio重新开始播放

>这就坑爹了，回头翻了下audio[相关的api](http://www.jianshu.com/p/816dfcd481dc)

3. 怎么添加类名？？？
>平时用jquery之类的dom操作库很方便就能添加类名，

>可是原生js是怎么添加类的。。只记得一个className

>查了下HTML5的[classList](http://www.zhangxinxu.com/wordpress/2013/07/domtokenlist-html5-dom-classlist-%E7%B1%BB%E5%90%8D/)