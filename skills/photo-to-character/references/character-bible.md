# 角色档案模板

用于同一角色跨照片、表情或动作复用。复制到用户项目的角色目录中填写；未知字段标为“不可见/待确定”，不要为填满表格编造事实。用户没有要求保存文件时，可先在本次上下文中保留简版。

```yaml
character_id: "用户指定的角色标识"
version: "1"
status: "draft" # 用户明确认可后改为 approved
identity_references: [] # 实际可访问的原照片路径
style_reference: null # 用户认可的画风参考
canonical_illustration: null # 用户认可的本角色标准图
fixed_features:
  species: null
  head_shape: null
  head_body_ratio: null
  ears: null
  eyes_shape_spacing_color: null
  nose_mouth: null
  body_shape: null
  tail: null
  markings_character_left: null
  markings_character_right: null
  distinguishing_features: []
palette: [] # 名称与色值；色值须来自实际取样或已明确的设计选择
outline:
  color: null
  relative_width: null # 相对画布/头宽记录，便于不同分辨率沿用
unknown_or_occluded: []
allowed_changes: ["姿势", "视角", "表情"]
```

避免将暖色灯光误认为毛色。多照片相互矛盾时，用清楚可见的中性光照片判断身份色，或沿用已认可色板。先复用标准图，再改变姿态；一次更换画风、比例、视角和表情会使一致性更难检查。

用户只要求单次转换时无需输出整份档案。不要把模型自行选中的结果标为用户已认可。
