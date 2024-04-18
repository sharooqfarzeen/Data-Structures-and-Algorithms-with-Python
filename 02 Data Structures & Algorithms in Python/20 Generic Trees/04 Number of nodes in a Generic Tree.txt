class TreeNode:
    def __init__(self,data):
        self.data=data
        self.children=list()

def printTree(root):
    #TNot a base case
    if root==None:
        return
    print(root.data)
    for child in root.children:
        printTree(child)

def printTreeDetailed(root):
    if root==None:
        return
    
    print(root.data,":",end="")
    for child in root.children:
        print(child.data,":",end="")
    print()
    
    for child in root.children:
        printTreeDetailed(child)

def takeTreeInput():
    print('Enter Root Data')
    rootData=int(input())
    if rootData==-1:
        return None
    
    root=TreeNode(rootData)
    
    print('Enter number of children for',rootData)
    childrenCount=int(input())
    for i in range(childrenCount):
        child=takeTreeInput()
        root.children.append(child)
    return root

def numNodes(root):
    if root==None:
        return 0
    count=1
    for child in root.children:
        count=count+numNodes(child)
    return count

root=takeTreeInput()
printTreeDetailed(root)
print(numNodes(root))