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
                      root = root.left    //然后查看左边:[1，2，4，6]装在stack里面
                  else:
                      cur = stack.pop()   // 若没有左边（root.left = none，才到else）则开始提取
                      res.append(cur.val) //加到回答里res = 1， stack = [2,4,6]
                      root = cur.right    //然后查看右边: 1.right = none, stack.pop(): res=[1,2];
                                            2.right = root =3, 上个if: stack = [+3,4,6]; 3.left = none
                                            cur = 3, res = [1,2,3]; 3.right = none; pop(4); cur = 4, stack = [6]
              return res
              
                                6
                              /   \
                             4     7
                            / \   / \
                           2   5 8   9
                          / \
                        1    3
