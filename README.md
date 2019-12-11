### 数据库相关
遵循gorm的惯例, 表结构中默认包含下列字段, 列名由字段名称进行下划线分割来生成:

```
// gorm.Model 定义
type Model struct {
  ID        uint `gorm:"primary_key"`
  CreatedAt time.Time // 列名为 `created_at`
  UpdatedAt time.Time
  DeletedAt *time.Time 
}
```

**注意:**
 - 1 如果模型有DeletedAt字段，调用Delete删除该记录时，将会设置DeletedAt字段为当前时间，而不是直接将记录从数据库中删除
 - 2 如果模型有 CreatedAt字段，该字段的值将会是初次创建记录的时间
 - 3 如果模型有UpdatedAt字段，该字段的值将会是每次更新记录的时间。