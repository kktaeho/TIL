# 오늘 배운 내용 작성
## 1026

```python
- 시도
class Solution:
    def maxAncestorDiff(self, root: Optional[TreeNode]) -> int:
        
    def counts(self, node):
        if node 0 :
            return
        if node != 0:
            node.val = node.left
            node.val = node.right

- 답
class Solution:
    def DFS(self, node, Ancestor):
        if not node:
            return -1
        if not Ancestor:
            Current = 0
        else:
            Current = max([abs(node.val - max(Ancestor)), abs(node.val - min(Ancestor))])
        LeftMax = self.DFS(node.left, Ancestor + [node.val])
        RightMax = self.DFS(node.right, Ancestor + [node.val])
        return max([Current, LeftMax, RightMax])
    def maxAncestorDiff(self, root: Optional[TreeNode]) -> int:
        return self.DFS(root, [])
```
