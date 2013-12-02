---
layout: post
title: 经典问题：你看源代码时，碰到过的"最好"的注释是怎样的？
---

译者注：这是一个来自 [Stackverflow](http://stackoverflow.com/questions/184618/what-is-the-best-comment-in-source-code-you-have-ever-encountered?page=2&tab=votes#tab-top) 上的问题，问题由于不符合 Stackoverflow 的社区规则，现在已经被关闭了; 之前也有别人翻译过，可是现在能搜到的翻译要不零散，要么翻译得不准确，这里特意选取了二十个来翻译，一起看看其中汇集了各式各样好玩的注释！

---

1.来自@[Jens Roland](http://stackoverflow.com/a/482129/769424)，得票数：1468 

对于注释，我总是感到愧疚，因为我总喜欢把非建设性的评论、代码诗和一些小笑话放到我自己的大部分项目中（尽管我自己认为会有足够的感知，能在代码发出去前删除掉明显冒犯性的内容）。这里是一个我自己特别喜欢的，放在很隐秘的地方且设计槽糕的"上帝对象"（God Object）：
  
```c
/*
* 至那些勇敢地探索到此处的伟大灵魂：
* 你就是那个冥冥中被选中的那个人，那个不懈地斟酌修改我们那些极其糟糕的代码的人，像是一个在编程世界里英勇的厮杀的骑士！
* 对你，对你这个真正的救世主，对你这个人类的王者，我郑重的说：
* never gonna give you up, never gonna let you down,
* never gonna run around and desert you. Never gonna make you cry,
* never gonna say goodbye. Never gonna tell a lie and hurt you.
*/ 
```
** (译者注：上面三句不翻译，其实是因为那是[一首歌](http://www.xiami.com/song/play?ids=/song/playlist/id/3431922/object_name/default/object_id/0)的歌词) **  
我很抱歉！！我实在忍不住不这么做啊...！！  
另外，还有一个，不过我并没有把它放出来，尽管我很想！！它存在于我写的一些不那么直观的类里面：  
  
```c
// 
// 亲爱的维护者：  
// 当你优化完这个程序时，你会明白你所做的优化是一个多么大的错误；  
// 请自觉在下面的累加器上留下记录，以提醒后来者：  
//  
//     total_hours_wasted_here = 42  
//   
```
  
---
  
2.来自@[benmatth](http://stackoverflow.com/a/549611/769424)，得票数：1058  
  
```c
Exception up = new Exception("真的出问题了！");  
throw up;  //哈哈哈哈  
``` 
  
---
  
3.来自@[johnc](http://stackoverflow.com/a/316233/769424)，得票数：1055  
  
```c  
//当我写下这些的时候，只有上帝和我知道我在做什么。  
//现在，只有剩下上帝知道了。  
```  
  
---  
  
4.来自@[Tuoski](http://stackoverflow.com/a/186309/769424)，得票数：1052  
  
```c  
stop(); // Hammertime!   
```  
  
** (译者注：这里的代码和注释其实连起来是一句[很有名的歌](http://www.xiami.com/song/play?ids=/song/playlist/id/1598992/object_name/default/object_id/0)里面的歌词) **  
  
--- 
  
5.来自@[Ash](http://stackoverflow.com/a/740603/769424)，得票数：1034  
  
这是为了防止某些笨蛋把我的代码混乱....  
  
```c  
// 这是自动生成的，请不要改变它。所有的改变将会被还原。  
```  
  
---

6.来自@[Sergey Kornilov](http://stackoverflow.com/a/185803/769424)，得票数：949

```c
// 有时候，我相信编译器会忽略我的全部注释
```

---

7.来自@[sharkin](http://stackoverflow.com/a/186967/769424)，得票数：933

```c
//我把这所有的代码、我所有的工作，奉献给我的妻子，Darlene,
//因为一旦这些代码被公开，她将不得不独自抚养我们的三个孩子、我和一只狗。
```

---

8.来自@[Tom Ritter](http://stackoverflow.com/a/184673/769424), 得票数：916

```java
// 为了保护傻逼，这些代码已经"消毒"过了
using System;
using System.Collections.Generic;
using System.Text;
using System.Reflection;
using System.Web.UI;

namespace Mobile.Web.Control
{
    /// <summary>
    /// 这是一个为配合那个名为 Richard 的傻逼工作的类!
    /// </summary>
    /// <remarks>（附注）
    /// 这是为了能让他那些设计糟糕的东西能在移动设备上正常工作，
    /// 主要的问题是他想那个 BindCompany() 方法能做任何事情，
    /// 我无奈得希望他死了。
    /// </remarks>
    public abstract class RichardIsAFuckingIdiotControl : MobileBaseControl, ICompanyProfileControl
         {
        protected abstract Pager Pager { get; }

        public void BindCompany(int companyId) { }

        public RichardIsAFuckingIdiotControl()
        {
            MakeSureNobodyAccidentallyGetsBittenByRichardsStupidity();
        }

        private void MakeSureNobodyAccidentallyGetsBittenByRichardsStupidity()
        {
            // 确保没有人会这真正使用那个傻逼 BinCompany 方法
            MethodInfo m = this.GetType().GetMethod("BindCompany", BindingFlags.DeclaredOnly | 
                BindingFlags.Instance | BindingFlags.Public | BindingFlags.NonPublic);
            if (m != null)
            {
               throw new RichardIsAFuckingIdiotException("No!! Don't use the fucking BindCompany method!!!");
            }
            // P.S. 这个方法只是一个玩笑， ... 下面那些就是来真的了。
        }

        /// <summary>（概括）
        /// 如果你希望这个控制语句能在这个请求内处理所有的事情，它就会返回真。  
        /// Richard 认为每次请求时重新加载整个网站的想法很好，认为进程事件应该自己结束自己；
        /// 他还认为头巾和飞行员眼镜是极其的奇形怪状的，哥们。
        /// </summary>
        protected bool IsThisTheRightPageImNotSureBecauseRichardIsDumb()
        {
            return Request.QueryString["Section"] == this.MenuItemKey;
        }

        protected override void OnLoad(EventArgs e)
        {
            if (IsThisTheRightPageImNotSureBecauseRichardIsDumb())
            {
                Page.LoadComplete += new EventHandler(Page_LoadComplete);
                Pager.RowCount = GetRowCountBecauseRichardIsDumb();
            }
            base.OnLoad(e);
        }

        protected abstract int GetRowCountBecauseRichardIsDumb();
        protected abstract void BindDataBecauseRichardIsDumb();

        void Page_LoadComplete(object sender, EventArgs e)
        {
            BindDataBecauseRichardIsDumb();
        }

        // 剩下的的他那些累赘的接口成员
        public abstract string MenuItemName { get; set; }
        public abstract string MenuItemKey { get; set; }
        public abstract bool IsCapable(CapabilityCheck checker, int companyId);
        public abstract bool ShowInMenu { get; }
        public virtual Control CreateHeaderControl()
        {
            return null;
        }
    }
}
```

更新：对这份代码的原作者也做了自己的[声明](http://mcfunley.com/from-the-annals-of-dubious-achievement)，我也会把他这应得的 credit 送出去。 我进去[Dan McKinley](http://mcfunley.com/)在的公司后，很快他就离职了。他对我说了更多的关于那份代码的背景和别的 Richard 写的"令人爆粗"的代码。

---

9.来自@[Rohit](http://stackoverflow.com/a/778275/769424)，得票数：830

```c
// 少许修改1 - 2002/6/7 增加临时地跟踪登录界面的设置
// 少许修改2 -  2007/5/22/ 临时个毛！
```

---

10.来自@[Daniel Papasian](http://stackoverflow.com/a/185181/769424), 得票数：728

```c
// 我喝醉了，迟些再修改。
```

我希望那时候我是在开玩笑；但我知道其他开发者这样写时，我认为那是认真的。

---

11.来自@[Jason Sundram](http://stackoverflow.com/a/185106/769424)， 得票数：722

```c
//里面有魔法的，别修改。
```

---

12.来自@[Sulik](http://stackoverflow.com/a/771974/769424), 得票数：703

```c
#define TRUE FALSE //祝你找BUG愉快，笨蛋！
```

---

13.来自@[Greg D](http://stackoverflow.com/a/184701/769424), 得票数：641

```c
// 很抱歉..
```

---

14.来自@[Lateral](http://stackoverflow.com/a/185308/769424), 得票数：637

```bash
return 1; #returns 1
```

---

15.来自@[Draemon](http://stackoverflow.com/a/185576/769424), 得票数：593

```c
/* 这里时间复杂度为 O(scary）, 但在实际应用中看起来足够快 */
```

接着是四个内嵌的for 循环语句...

---

16.来自@[Randyaa](http://stackoverflow.com/a/184682/769424), 得票数：509

```c
Catch (Exception e) {
  //谁真会关心这个？
} 
```

---

17.来自@[martinus](http://stackoverflow.com/a/389723/769424), 得票数：496

```java
 /**
 * 总是返回真的！
 */
 public boolean isAvailable() {
     return false;
 }
```

永远不要相信注释......

---

18.来自@[PoppaVein](http://stackoverflow.com/a/189859/769424), 得票数：458

```c
/*
* 你或者会觉得你知道下面这些代码是做什么的。
* 但你不会知道的，相信我。
* 瞎搞瞎改，你得到的只是很多个不眠之夜，你不要以为你很聪明，能"优化"下面那些代码。
* 关掉这个文件，玩别的去吧。
*/
```

---

19.来自@[gedevan](http://stackoverflow.com/a/192823/769424), 得票数：431

```c
try {
 
} finally { // 按道理说，这个不应该发生。

}
```

---

20.来自@[Juliano](http://stackoverflow.com/a/615845/769424), 得票数：355

```c
long long ago;  /* 在那遥远浩瀚的银河深处... */ 
```

还有更多的注释可以直接去[原问题](http://stackoverflow.com/questions/184618/what-is-the-best-comment-in-source-code-you-have-ever-encountered)下面翻。

---

本文由 [JeOam](http://jeoam.github.io) 翻译,  首发于 [SegmentFault](http://segmentfault.com/a/1190000000345897) 社区。
