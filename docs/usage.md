# Corecos Usage 
## Running the Project

=== "Run Project on Preview Mode (localhost)"
    1. Set up ENV in `env.preview.local` from `./extensions/corecos/env`
    2. Set up Configs in `config.preview.custom.ts` from `./extensions/corecos/src/configs`
    3. Run this script to build the bundle in preview mode: `bun preview`
    !!! note "Run this script only once. If you need to update ENV or Configs, run it again."

=== "Run Project on Local (Development Build Mode)"
    1. Import build config in Cocos Build from: `./configs/buildConfig_localhost.json`
    2. Set up ENV in `env.browser.local` from `./extensions/corecos/env`
        - Set `GAME_SDK = null`
    3. Set up Configs in `config.browser.custom.ts` from `./extensions/corecos/src/configs`
    4. Run this script to build the bundle: `bun build:localhost`
        - !!!note "If you only need to test the build flow, run `bun build:localhost --sbg` to skip building the game."
    5. Open this link in a browser: http://127.0.0.1:7456/web-mobile/localhost/index.html
        - !!!note "Open Cocos Creator with your project before opening this link."

=== "Run Project on Web (Production Build Mode)"

    - Guide for Facebook Instant Game
        1. Import build config in Cocos Build from: `./configs/buildConfig_facebook.json` (only first time)
        2. Set up ENV in `env.facebook.local` from `./extensions/corecos/env`
            - Set `GAME_SDK = https://connect.facebook.net/en_US/fbinstant.7.1.js` for Facebook Instant Game
            - !!!note "If it doesn't exist, please check flow `Initialize Corecos`"
        3. Set up Configs in `config.facebook.custom.ts` from `./extensions/corecos/src/configs`
            - !!!note "If it doesn't exist, please check flow `Initialize Corecos`"
        4. Check your code: `bun util:check` and `bun util:unused`
        5. Run this script to build game: `bun build:facebook`
            - !!!note "Check build log, if there's an error, you need to fix it first."
        6. When all done, use `bun deploy:fb` to archive and upload to host.
            - !!!note "Check build log, to continue guide."
            - !!!note "`:fb` is has `auto-version` feature, and `:facebook` is not."