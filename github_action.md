# 手动触发GitHub Action

- 需要 Github token
- https://github.com/settings/tokens/new  直接新建一个token

#### 变量说明
```bash
# TOKEN:     github token
# TYPE_NAME: 自定义 Webhook 事件名称
# BRANCH:    触发action分支名
# OWNER:     GitHub用户名
# REPO:      所触发action的仓库名
# ID:        workflowsID
```

### workflow_dispatch 方法
- 需要添加 workflow_dispatch 到yml文件里面

```bash
curl -H "Content-Type:application/json" -X POST \
-d '{"inputs": {}, "ref":"BRANCH"}' \
-H "Authorization: token TOKEN" \
https://api.github.com/repos/:OWNER/:REPO/actions/workflows/:ID/dispatches 
```

### repository_dispatch
> 要触发自定义 repository_dispatch web 挂钩事件，必须将 POST 请求发送到 GitHub API 端点，并提供 event_type 名称来描述活动类型。 要触发工作流程运行，还必须配置工作流程使用 repository_dispatch 事件。

- 添加 repository_dispatch 到yml文件， 参考[create-a-repository-dispatch-event
](https://docs.github.com/cn/rest/reference/repos#create-a-repository-dispatch-event)

```bash
curl -H "Accept: application/Accept: application/vnd.github.v3.full+json" \
-H "Authorization: token TOKEN" \
--request POST \
--data '{"event_type": "TYPE_NAME"}' \
https://api.github.com/repos/:OWNER/:REPO/dispatches
```
