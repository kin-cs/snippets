# snippets
The sinppets I use/make, mainly for automation.

Chinese vocab counter
---

```python
import re
import pandas as pd

my_context = '''
液体ye 4

酒 jiu

广告 guang3

做 zuo4

课ke4

奴隶 li4

液体 ye 4

沸点fei4

两边 liang

锅 guo1

是 shi

那本 na4 那么 na4

之 zhi1

借口 jie4

脑nao3

星 xing'''

my_words_dict = {}

for n in re.findall(u'[\u4e00-\u9fff]+',my_context):
    print(n)
    my_words_dict[n] = my_words_dict.get(n, 0) + 1

sorted_by_value = sorted(my_words_dict.items(), key=lambda kv: kv[1])

sorted_by_value.reverse()

df = pd.DataFrame(columns=['vocab', 'times'])

for i, j in sorted_by_value:
    print(i, j)
    a = pd.DataFrame([[i, j]],columns=['vocab', 'times'])
    df = df.append(a, ignore_index=True)

df.to_excel('mandarin_vocab.xls')

```
