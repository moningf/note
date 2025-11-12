---
tags:
  - python
  - py_api
---
```python
import json
#准备符合=json的py数据
date = [{"name":林},{"age":18}]

#将py数据转换为json数据
date = json.dumps(date)
#将其不使用ascii来转换,直接把内容输出出来
#indent用来美好格式,表示缩进
#date = json.dumps(date,ensure_ascii=False,indent=4)

#将json数据转换为py数据
date = json.loads(date)
```