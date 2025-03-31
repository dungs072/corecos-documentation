All the thing you should know will be here.
## Banner Ad height
- You should put the block lines of code in a script (such as GameScene.ts) for retrieving easily
    ```ts
    window.game.ads
    .showBannerAdAsync(GameCore.Configs.Ads.BannerDisplayAdOptions[0].PlacementId)
    .catch((error) => {
        console.warn('showBannerAdAsync', error)
    }) 
    ``` 
- If the banner ad does not show you may try this. Go to `MockBannerInstance.ts`. Update `getAdContentAsync()` function with this one
    ```ts
        private async getAdContentAsync(): Promise<string> {
        const response = await fetch(this.apiAdContent, { method: 'GET' })
 
        const json = await response.json()
 
        if (!('data' in json)) return ''
 
        if (!Array.isArray(json.data)) return ''
 
        const images = json.data as { images: { downsized: { url: string } } }[]
        const rand = Math.floor(Math.random() * images.length)
 
        return images[rand].images.downsized.url
    }
    ```
## Debugger
- You can run any event of project game when it registers in the scene in web console with this command: 
    ``` ts
        cc.director.getScene().emit('event-name')
    ```