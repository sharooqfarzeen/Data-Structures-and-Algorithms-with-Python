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

def numLeafNodes(root):
    if root==None:
        return 0
    if root.left==None and root.right==None:
        return 1
    numLeafLeft=numLeafNodes(root.left)
    numLeafRight=numLeafNodes(root.right)
    return numLeafLeft+numLeafRight

root=treeInput()
printTreeDetailed(root)
print(numLeafNodes(root))