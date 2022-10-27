# leet94-biDFS-inorder

算完所有的左边，然后再加上所有的右边

# recursive-太快了:

      def inorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
          if not root:
              return []

          return self.inorderTraversal(root.left) + [root.val] + self.inorderTraversal(root.right)

          # always starts from left
  
  
 #  iterative：
  
