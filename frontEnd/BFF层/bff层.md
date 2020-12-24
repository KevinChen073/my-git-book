<!--
 * @Author: 星啸(陈远宏)
 * @Date: 2020-12-15 14:32:55
 * @LastEditTime: 2020-12-23 23:42:04
 * @LastEditors: 星啸(陈远宏)
 * @Description: 
 * @FilePath: /my-git-book/frontEnd/BFF层/bff层.md
-->
## BFF层
BackEnd For FrontEnd，服务于前端的后端。也就是业务聚合层。https://www.jianshu.com/p/eb1875c62ad3

### 优劣
劣：要求前端需要的技能更加多了，但如果能够陪着serverless等体系考虑，其实也无不可。
优：
- 排错、业务逻辑组合等都能够更好的组合。
- 性能优化：针对多个首屏接口的编排，在服务端组合肯定比前端要快。
- 同时面临的前端话语权不足，业务参与不深的问题也可以得到缓解。
