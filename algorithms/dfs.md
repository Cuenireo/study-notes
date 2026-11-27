# 算法：DFS，深度优先搜索

```python
def dfs(graph, node, seen=None):
    if seen is None:
        seen = set()
    seen.add(node)
    print(node, end=" ")
    for nxt in graph.get(node, []):
        if nxt not in seen:
            dfs(graph, nxt, seen)

dfs({"a": ["b", "c"], "b": ["d"], "c": [], "d": []}, "a")
# a b d c
```

- DFS 一条路走到黑，走不通再回溯，递归写起来最直观。
- 迷宫、拓扑排序、连通分量都是 DFS 的典型应用。
- 递归深度有限制（Python 默认 1000），深图用显式栈改迭代版。
- 注意 `seen=None` 的写法：别用可变对象当默认参数。
