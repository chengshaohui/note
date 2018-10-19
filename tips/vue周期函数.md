| 生命周期函数  | 描述                                               | 作用                                               |
| ------------- | -------------------------------------------------- | -------------------------------------------------- |
| beforeCreate  | 组件实例刚被创建，el 和 data 并未初始化            | 在这加个loading事件                                |
| created       | 组件实例创建完成，完成了 data 数据的初始化，el没有 | 在这结束loading，还做一些初始化，实现函数自执行    |
|               |                                                    |                                                    |
| beforeMounted | 模板编译/挂载之前，完成了 el 和 data 初始化        |                                                    |
| mounted       | 模板编译/挂载之后，完成挂载                        | 在这发起后端请求，拿回数据，配合路由钩子做一些事情 |
|               |                                                    |                                                    |
| beforeUpdate  | 组件更新之前                                       |                                                    |
| updated       | 组件更新之后                                       |                                                    |
|               |                                                    |                                                    |
| beforeDestroy | 组件销毁前调用                                     | 你确认删除XX吗？                                   |
| destroyed     | 组件销毁后调用                                     | 当前组件已被删除，清空相关内容                     |
|               |                                                    |                                                    |
| activated     | for ==keep-alive==，组件被激活时调用               |                                                    |
| deactivated   | for ==keep-alive==，组件被移除时调用               |                                                    |

参考链接：[vue生命周期简介](https://segmentfault.com/a/1190000008010666#articleHeader0)