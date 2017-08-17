swift中的访问权限

访问控制模型基于模块源文件

internal：内部的 

1. 默认情况下所有的类，属性方法的访问权限都是internal
2. 在本模块\(项目、包、target\)中可以访问

private：私有的

1. 只在本类中可以访问

open：公开

1. 可以跨模块都可以访问

fileprivate：swift3.0

1. 只要是在本文件中都是可以访问的



