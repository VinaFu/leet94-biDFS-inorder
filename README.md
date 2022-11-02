# leet94-biDFS-inorder

算完所有的左边，然后再加上所有的右边

# recursive-太快了:

      def inorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
          if not root:
              return []

          return self.inorderTraversal(root.left) + [root.val] + self.inorderTraversal(root.right)

          # always starts from left
  
  
  
  
 # iterative：

      class Solution:
          def inorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
              stack = []                  //stack就是用来暂时装东西的
              res = []                    // 这才是最终的回答地点
              while stack or root:        // 如果stack和root存在，不然则是空集。
                  if root:
                      stack.append(root)  //若存在root，先盒子里（stack）放好
                      root = root.left    //然后查看左边，毕竟他是第一个
                  else:
                      cur = stack.pop()   // 若没有左边了（因为root.left = none，才到else）则开始提取盒子里的值
                      res.append(cur.val) //并加到回答里
                      root = cur.right    //然后查看右边，然后重复上面。
              return res
