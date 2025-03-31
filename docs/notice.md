You should notice that because this is my experience while working with this extension, typescript, cocos, game industry
### Avoid using setTimeOut()
- You can use node.scheduleOnce() or node.schedule()
### Avoid change or modify anything in corecos extension
- If you find bugs or something weird. Please contact to Mr. WON for more information
### Node should build like a tree 
- You cannot drag script in a node that is a child of node A to the other nodes that has same level with node A
- The parent node can access to any child node (even scripts). Children nodes can only access in their scope only.
### How to delete the cache
- clear cache at `application -> clear data` on web
- 

