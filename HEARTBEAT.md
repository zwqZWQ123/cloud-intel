# Heartbeat 任务清单

## 每日定时任务 (08:00 上海时区)

五大云动态采集任务 - 每天 08:00 执行：

1. **采集 AWS**：从 `https://status.aws.amazon.com/rss/all.rss` 抓取过去24小时状态事件
2. **采集 Azure**：从 `https://azure.microsoft.com/en-us/updates` 抓取产品更新（无RSS，需网页抓取）
3. **采集 阿里云**：从 `https://www.aliyun.com/product/news` 抓取产品动态
4. **采集 腾讯云**：从 `https://cloud.tencent.com/announce/` 抓取公告
5. **采集 华为云**：从 `https://www.huaweicloud.com/announcements/` 抓取服务公告
6. **生成报告**：写入 `cloud-intel/daily/YYYY-MM-DD.md`
7. **推送结果**：发送到当前 QQ 窗口

---

## 执行流程

当收到 heartbeat 触发时：
1. 使用 browser/web_fetch 工具抓取各云厂商页面
2. 解析并筛选过去24小时的动态
3. 按优先级分类（高/中/低）
4. 生成 Markdown 报告
5. 发送摘要到 QQ 窗口