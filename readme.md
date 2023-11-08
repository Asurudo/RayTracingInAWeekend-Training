# Ray Tracing in a Weekend - Training

## 环境
开发环境：Viscual Studio Code

编译环境：GCC

## 介绍

不借助任何非官方库，全部采用C++编写的光线追踪小玩具。

基本思想将照相机（观察点）作为原点，以从原点到最终成像的画布上的每个像素点作为射线方向，将该射线看作一条光线。该光线进行不断反射和折射，最后求得画布上该像素点的颜色。

其中最为关键的步骤有两点：光线对物体的碰撞、以及根据物体材质的不同，光线的反射/折射具体方向。

对于碰撞的计算，假设这个世界只存在圆球，因此对于某一条光线，可以遍历所有圆球，转换成一元二次方程组解的数量来判断光线是否撞上圆球。

对于反射和折射的方向，本玩具为圆球设置了三种材质，分别为漫反射材质、金属材质以及电解质（看起来透明的材质）三种：
1. 漫反射材质，光线的反射方向是不确定的，因此随机向一个方向反射。
2. 金属材质，基本是严格的镜面反射。当镜面反射不严格、即模糊系数较高时，反射的方向向旁边偏移。
3. 电解质材质，考虑到了折射的情况，通过入射角度和材质的折射率确定折射方向（也有可能发生全反射现象）。

细节见笔记与代码注释。

## 最终效果图

![](https://www.z4a.net/images/2023/11/07/QQ20231107153255.md.png)

## 参考资料

[In One Weekend](http://in1weekend.blogspot.com/)

[Ray Tracing in a Weekend 阅读笔记](https://asurudo.top/s/BFf69NS5a)