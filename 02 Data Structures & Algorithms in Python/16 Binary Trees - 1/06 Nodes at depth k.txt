class BinaryTreeNode:
    def __init__(self,data):
        self.data=data;
        self.left=None
        self.right=None

def printTree(root):
    if root==None:
        return
    print(root.data)
    printTree(root.left)
    printTree(root.right)

def printTreeDetailed(root):
    if root==None:
        return
    print(root.data,end=":")
    if root.left!=None:
        print("L",root.left.data,end=",")
    if root.right!=None:
        print("R",root.right.data,end="")
    print()
    printTreeDetailed(root.left)
    printTreeDetailed(root.right)

def treeInput():
    rootData=int(input())
    if rootData==-1:
        return None
    root=BinaryTreeNode(rootData)
    leftTree=treeInput()
    rightTree=treeInput()
    root.left=leftTree
    root.right=rightTree
    return root

def printDepthK(root,k):
    if root==None:
        return
    if k==0:
        print(root.data)
        return
    printDepthK(root.left,k-1)
    printDepthK(root.right,k-1)

def printDepthKV2(root,k,d=0):
    if root==None:
        return
    if k==d:
        print(root.data)
        return
    printDepthKV2(root.left,k,d+1)
    printDepthKV2(root.right,k,d+1)

root=treeInput()
printTreeDetailed(root)
printDepthKV2(root,2)