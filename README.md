<!--
 * @Author: LetMeFly
 * @Date: 2025-01-28 14:59:48
 * @LastEditors: LetMeFly.xyz
 * @LastEditTime: 2025-01-28 16:05:24
-->
# secret-monitor-tester

test repo [secret-monitor](https://github.com/LetMeFly666/secret-monitor)

## 测试指标

1. 新增commit时，检测最后一次commit中是否包含秘密信息
    + 若包含：Action直接运行失败✅
    + 否则（不包含密钥信息）：Action运行成功
2. 新增PR/PR关闭后重启时，检测PR中所有commit，若包含秘密信息，在PR中评论所有秘密信息所在位置并且Action运行失败
3. 往开启的PR中新增commit时，检测新增commit和所有commit。
    + 若新增commit不包含秘密信息：
        + 若旧commit中仍包含秘密信息，则评论提醒删除旧commit信息并且Action运行失败
        + 否则Action运行成功
    + 否则（新commit包含秘密信息）：评论新增commit中秘密信息所在位置并且Action运行失败