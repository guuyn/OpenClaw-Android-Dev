# 记忆系统 Lite 设计规范

> 版本: v1.0 | 日期: 2026-04-02 | 设计者: WSL2 (guyan)

## SQLite 表结构

```sql
-- 用户偏好表
CREATE TABLE preferences (
    key TEXT PRIMARY KEY,
    value TEXT NOT NULL,
    category TEXT DEFAULT 'general',
    created_at INTEGER NOT NULL,
    updated_at INTEGER NOT NULL
);

-- 关键决策表
CREATE TABLE decisions (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    topic TEXT NOT NULL,
    decision TEXT NOT NULL,
    context TEXT,
    confidence INTEGER DEFAULT 100,
    created_at INTEGER NOT NULL
);

-- 任务状态表
CREATE TABLE tasks (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    type TEXT NOT NULL,
    description TEXT NOT NULL,
    status TEXT NOT NULL,
    checkpoint TEXT,
    result TEXT,
    created_at INTEGER NOT NULL,
    updated_at INTEGER NOT NULL
);
```

## 接口定义

```kotlin
interface MemoryManager {
    suspend fun getPreference(key: String): Preference?
    suspend fun setPreference(key: String, value: String)
    suspend fun addDecision(topic: String, decision: String)
    suspend fun createTask(type: String, description: String): Long
    suspend fun getPendingTasks(): List<Task>
    suspend fun extractAndStore(message: String, role: String): List<String>
}
```

---

*完整规范见 workspace*