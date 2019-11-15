 ## js盒子模型  
         style为行内样式，样式表中的样式，style是获取不出来的

        getComputedStyle:计算后的样式

        要获取样式表中的样式可以使用
            getComputedStyle(element).attr

            *注意:
                这个方法获取的值是带单位的

        有时候需要隐藏某个元素，但是又要存一个当前元素的尺寸，这个时候使用getComputedStyle


        下面的属性结果都为不带单位的数字：
            clientWidth/clientHeight   盒子可视的宽度(支持padding)

            clientLeft/clientTop   左边框和上边框


            offsetWidth/offsetHeight   盒子可视的宽度(支持padding + border)
            offsetParent  定位父级(元素)
            offsetLeft/offsetTop  定位父级到当前元素的距离（当前元素的左外边框到定位父级的左内边框的距离）

            scrollHeight被内容撑开的高度,不算边框的

             offsetLeft/offsetTop在实际中(页面复杂的情况下，要慎用，获取的距离是根据定位父级来的)

            绝对位置才是最稳的一个距离（当前元素到页面顶部的距离）

            思路:
                求得绝对位置，就是把当前元素的所有祖先节点的距离计算一遍，求和即可

            具体实施:
                1.先定义一个元素（作为当前元素）
                2.先求当前元素的距离（包含定位距离和边框距离）
                3.把这次的定位父级变成下一次循环的当前