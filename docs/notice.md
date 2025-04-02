You should notice that because this is my experience while working with this extension, typescript, cocos, game industry
### Avoid change or modify anything in corecos extension as much as possible
- If you find bugs or something weird. Please contact to Mr. WON for more information
### Avoid using setTimeOut()
- You can use node.scheduleOnce() or node.schedule()
### Node should build like a tree 
- You cannot drag script in a node that is a child of node A to the other nodes that has same level with node A
- The parent node can access to any child node (even scripts). Children nodes can only access in their scope only.
### How to delete the cache (do it in order until no errors)
- Use this in devtool `cc.game.emit('clear-hybrid-file-cache')`
- Clear cache at `application -> clear data` on web (devtool)
- In cocos editor, go to `Developer -> Cache -> Clear code cache`
- Delete 3 folders in project: profile, temp, library and then reopen cocos again
### Meta file
- Meta file can be created by creating a new folder 
### How to check bundle size of game
- Open game on facebook
- Open devtool -> Network
- Choose one asset of a game
- Copy link (such as: `https://apps-1485269139041031.apps.fbsbx.com/br-compress-instant-bundle`) and paste it in filter
- Reload game again
### Lazy load
- Definition: Player still can play game while the data is loading
- Lazy load: sprite, prefab, audio,...
### Do not use object.entries.foreach or foreach
- You can use for...of... instead
### How to build efficient game play
- You should separate logic game and animation into two part
### Link to run your game faster and code changes -> game reload again
- http://localhost:7456/?no-toolbar=1&no-vconsole=1&auto-resize=1&auto-refresh=1
!!!note "Please change the port relatively"
### Particle effect
- Texture use for particle should turn off Packable
- Texture of particle cannot be packed in atlas
### Build localhost
- Always name the folder is `localhost`
### Config size for game
- You can change config size of game (landscape, portrait) in `GameWord.ts`
### Delete the old facebook app id
- Go to `configs -> fb-deploy-config.json`. Delete file `fb-deploy-config.json`
!!!note "This file will be generated automatically when you run core-init again" 
### Canvas
- Do not leave the camera property in canvas blank. Assign camera to it
### Spine
- Must use lazy load to load spine
- Turn off Premultiplied alpha when use spine
- Turn on spine and add manually in `Cocos editor -> Project settings -> Feature cropping`
- Go to boot scene -> Turn on `loadWasmModuleSpine()` and make sure instantiate after loadWasmModuleSpine finished (lazy load spine)

