# 鉴权Token

使用JWT作为鉴权Token。基于JWT标准文档，我们根据我们的业务场景做一些拓展。

预期特性：
- 支持user_id和secret_id两种JWT的sub机制，且JWT可识别使用哪种（或哪些）方式验证。
- 支持user_id机制下灵活拓展，以方便加入安全机制。
- 保证secret_id机制简单且安全。