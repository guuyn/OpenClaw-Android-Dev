# 任务队列 Lite 设计规范

> 版本: v1.0 | 日期: 2026-04-02 | 设计者: WSL2 (guyan)

## 数据结构

```kotlin
data class AgentTask(
    val id: Long = 0,
    val type: String,
    val description: String,
    val priority: Int = 0,
    val skills: List<String>,
    val systemPrompt: String?,
    val input: String,
    val status: TaskStatus = TaskStatus.PENDING,
    val progress: Int = 0,
    val result: String? = null
)
```

## 接口定义

```kotlin
interface TaskQueue {
    suspend fun submit(task: AgentTask): TaskHandle
    suspend fun getTask(taskId: Long): AgentTask?
    suspend fun getRunningTasks(): List<AgentTask>
    suspend fun cancelTask(taskId: Long): Boolean
}
```

---

*完整规范见 workspace*