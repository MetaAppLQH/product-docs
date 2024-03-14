# 力区域

::: tip **阅读本文预计 10 分钟**
**本文概述了编辑器中力区域对象的相关定义及使用方法。**
:::


## 什么是力区域对象
> 力区域对象自身是在一个体积,对进入体积内的具有物理模拟特性的对象施加一个平行力或径向力,使其发生物理模拟运动.



## 力区域对象属性

### 区域设置

| 属性     | 说明                                                 |
| -------- | ---------------------------------------------------- |
| 自动启用 | 设置是否启用区域物理效果,禁用状态下,不会应用力到物体上. |
| 施力类型 | 设置区域内力的应用方式.  |
| 力值 | 设置区域内物理力的大小.  |

### 施力类型

| 属性   | 说明                         |
| ------ | ---------------------------- |
| 指向力 | 向某个方向施加一个冲量 |
| 径向力 | 以圆心向外施加一个冲量 |


## 如何使用力区域对象

1.在本地资源库中搜索[力区域对象],找到功能对象,拖入到场景中即可完成创建.
2.在属性面板中设置区域内力的效果,力值可参照当前世界重力加速度 * 对象自身质量.


## 力区域对象高级使用方法

### 力区域对象回调

```ts
@Component
export default class NewScript1 extends Script {

    /** 当脚本被实例后，会在第一帧更新前调用此函数 */
    protected onStart(): void {

        let forceVolumeMain = this.gameObject as ForceVolume;

        //力区域对象提供了回调方法
        forceVolumeMain.onEnter.add((chara: Character) => {
            console.log(`角色进入力区域范围`);
        })
        forceVolumeMain.onLeave.add((chara: Character) => {
            console.log(`角色离开力区域范围`);
        })
    }
}
```
<video controls src="https://cdn.233xyx.com/athena/online/85157428cd8e46438b57df1abb2fd79f.mp4"></video>