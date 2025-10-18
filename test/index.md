# Test

## 269. Alien Dictionary
Below is a dfs solution to the alien dictionary problem.
```python
    def alienOrder(self, words: List[str]) -> str:
        letter_graph = defaultdict(set)
        indegree_map = {l: 0 for w in words for l in w}

        for w1, w2 in zip(words, words[1:]):
            for l1, l2 in zip(w1, w2):
                if l1 != l2:
                    if l2 not in letter_graph[l1]:
                        letter_graph[l1].add(l2)
                        indegree_map[l2] += 1
                    break
            else:
                if len(w2) < len(w1): return ""
      
```

<!--more-->


---

> Author: Yeu-Chern Harn  
> URL: http://localhost:1313/test/  

