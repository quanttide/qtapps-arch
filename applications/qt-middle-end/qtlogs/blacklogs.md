# 待评估需求

- 日志系统增加云托管版本功能。对每一次请求，记录这个用户访问的云托管版本，方便后台统计灰度过程中后台是否正常运行，也方便数据分析做AB测试。技术实现需要接入云开发的Python SDK。需要明确场景在哪里以评估是否必要。
- 为所有微服务增加requestID，考虑使用 https://pypi.org/project/wsgi-microservice-middleware。如果可以读取腾讯云的requestID则不需要再自己做。考虑在日志服务中记录每一笔requestID。具体使用场景尚不明确，不好评估必要性及投入产出比。
