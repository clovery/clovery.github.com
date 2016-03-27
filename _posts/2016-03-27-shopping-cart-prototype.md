---
title: 关于购物车原型的分析
---

接手有关移动端商城的项目，有关于购物车模块的设计，既有的实现，遇到一些问题，值得拿出来思考下。

关于购物车数据的存储，业界最佳实践是存储在服务器端。存储在服务器端最大的好处是能够实现多平台数据的同步。

然而，对于这个项目来说，却反其道而行，使用 `localStorage` 把数据存储在本地。忍了。

商城是提供给其他第三方小商户使用的，然而，购物车竟然是跟商户联系在一起的，也就是说，从一个商户买了点东西放到了购物车，切换到另外的商户，又加了点东西进去，然后去往购物车结算的时候，上一个商户中添加的数据，对于用户来说就清空了，清空了？？？

好吧，好吧，只能默默无言。(╯‵□′)╯︵┻━┻

总结槽点如下：

1. 使用 `localStorage` 保存购物车数据，数据存储脆弱
2. 购物车对应商户，而非用户，容易造成混淆

既然没法在源头上解决这个问题，那么只能思考如何设计购物车，才能实现最大程度的扩展。

## 首先要解决购物车数据采用的数据结构存储的问题。

先前的实现中将所有商户的购物车数据存储在一起，在切换商户的同时过滤数据，获得该商户下的购物车数据。

这种实现的缺点是数据混合在一起，操作起来不方便，切换商户都要去过滤数据。而且对于增删改查这样的操作，只能过滤出来对应的数据，才能做处理，灵活度不够高。

既然每个商户都有一个购物车数据，那么从这里出发的话，可以为每个商户构造对应的购物车。形式如下：

    cart_[id]: {
      [id]: {
        id: '商品Id',
		  name: '商品名称',
		}
    }


在这种数据结构中，以商户的 `id` 作为变量，存储在 `localStorage` 中，以商品的 `id` 作为存储的键，方便数据的查询。

从而解决了数据过滤这种低效且容易造成混淆的操作。

## 将购物车对象和购物车存储拆分

* CartService
* CartStorageService
