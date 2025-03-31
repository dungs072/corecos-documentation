# Corecos Setup 

## 🚀 Initial Setup

- Choose Package Manager
    - You can use either Yarn or Bun as your package manager. Ensure you have one of them installed:
        - [Yarn Installation Guide](https://classic.yarnpkg.com/en/docs/install)
        - [Bun Installation Guide](https://bun.sh/)

- Add Corecos Repository
    - Add the remote repository: `git remote add corecos [git@corecos-repo-link]`
    - Pull the latest code: `git pull corecos master`

- Setup Corecos Submodule (Admin Only)
    - Initialize submodules if it's your first time: `git submodule update --init && git submodule update --remote` (only first time)
    - Update submodules otherwise: `git submodule update`

## 🔥 Initialize Corecos

=== "Understanding Environment and Config Inheritance"

    - **Environment Files (`./extensions/corecos/env`)**: These files define environment-specific variables that are used during the build and runtime processes. The inheritance follows this order:
        - `.env`: Base environment settings.
        - `.env.preview` or `.env.browser`: Specific settings for preview or browser environments.
        - `*.local`: This is custom environment for same platform, e.g., `env.browser.local` for localhost.
        - Platform-specific overrides (e.g., `env.browser.local` -> `env.facebook.local`, `env.msgames.local`, etc.): These files provide additional or overriding settings for specific platforms.

    - **Configuration Files (`./extensions/corecos/src/configs`)**: These files define game-specific configurations. The inheritance follows a similar pattern:
        - `config.defaults.ts`: Base configuration settings for the game.
        - `config.preview.defaults.ts` or `config.browser.defaults.ts`: Specific settings for preview or browser environments.
        - `*.custom.ts`: This is custom config for same platform, e.g., `config.browser.custom.ts` for localhost.
        - Platform-specific overrides (e.g., `config.browser.custom.ts` -> `config.facebook.custom.ts`, `config.msgames.custom.ts`, etc.): These files provide additional or overriding settings for specific platforms.

=== "Initialize Corecos"
    1. Install dependencies: `bun install`
        - Note: If you get an error about `node_modules` not found, run `yarn install` in `./extensions/corecos`.
    2. Run the CLI to initialize core: `bun init:core`
        - Note: You can initialize a specific platform, e.g., `bun init:core --to facebook`
        - Note: You can force initialize a specific platform, e.g., `bun init:core --to facebook --force`
    3. Build the extension: `bun build:extension` (run twice if it's your first time)
    4. Update your game name in `./extensions/corecos/env/env.local`
        - Example: `VITE_GAME_NAME = Save The Pets`
    5. Set up the `auto-version` feature by setting `VITE_BUILD_VERSION = 0` in an ENV file.
        - Example: `./extensions/corecos/env/env.browser.local` - for localhost
        - Example: `./extensions/corecos/env/env.facebook.local` - for Facebook Instant Game
    6. Update your `AppId` for the live version in a config file.
        - Example: `./extensions/corecos/src/configs/config.browser.custom.ts` - for localhost
        - Example: `./extensions/corecos/src/configs/config.facebook.custom.ts` - for Facebook Instant Game

## 🎮 Enable Corecos Extension

- Build the extension: `bun build:extension`
!!! note "You may need to run this script every time you pull new code from corecos"
- Open Cocos Creator with your project.
- Open `Extension Manager`, click `Installed`, and enable the `corecos` extension.
!!! note "The `corecos` extension is enabled by default; check if needed."
- Close and reopen Cocos Creator.
!!! note "If you use `Reload` in the `Developer -> Reload` menu, you need to run `Reload` in the `Corecos -> Reload` menu."

## 🏗️ Setup Game Project (first time)
=== "Preview Mode"
    1. Add your Corecos game folder to the Cocos Dashboard.
        - Install Cocos Dashboard: https://www.cocos.com/en/dashboard
        - Install Engine version: 3.8.5
    2. Open Cocos Creator with your project.
    3. Ignore console errors; you may need to run `Reload` from the `Corecos -> Reload` menu.
    4. Proceed to: `Run Project on Preview Mode`

=== "Build Mode"
    1. Open the Build popup (Ctrl + Shift + B).
    2. Import a build config in Cocos Build from: `./configs/buildConfig_localhost.json`
        - Click `New Build Task`, select `Platform: Web Mobile`, and click `Import Build Config`.
        - Note: If the config is not for web-mobile, select the correct platform first.
        - Note: If import twice, you need to check correct build path in `Build Path` field.
    3. Run the build for the first time; Cocos Creator will save your build config.
        - Note: You may click the cancel button to stop the draft build.
    4. Update your Cocos Creator path in `./extensions/corecos/env/env.local`
        - Example (Windows): `COCOS_CREATOR_PATH = C:\ProgramData\cocos\editors\Creator\3.8.5\CocosCreator.exe`
        - Example (Mac): `COCOS_CREATOR_PATH = /Applications/Cocos/Creator/3.8.5/CocosCreator.app/Contents/MacOS/CocosCreator`
    5. Proceed to: `Run Project on Local`

## 📜 Explanation of cmds

=== "Core Commands"
    - `bun init:core`: Initialize corecos to create local env and custom config files.
    - `bun build:extension`: Build the extension for Cocos Creator.
    - `bun preview`: Build the bundle for preview mode.

=== "Build Commands"

    - Base Format for Build Commands:
        - `bun build:localhost`: Build the game for localhost (production).
        - `bun build:lc`: This is the same as `bun build:localhost`, but it has `auto-version` feature.
        - `bun version:lc`: Auto-build version for localhost.
        - `bun rollback:lc`: Rollback version for localhost.

    - Additional Format for Build Commands:
        - `bun upload:fb`: Only run upload archive by build version to host for Facebook Instant Game.
        - `bun deploy:fb`: Build the bundle, archive, and upload to host for Facebook Instant Game.
    !!! note "For other platforms, you can use the same format for build commands."

        Example: `bun build:android` or `bun build:ad` for Android


=== "Arguments for Commands"
    - `--sbg`: Skip building the Cocos game.
    - `--sbc`: Skip building corecos.
    - `--kcc`: Kill Cocos Creator before building, helpful if the build always gets stuck.
    - `--bbo`: Build bundle only, reducing build time.
    - `--to`: Build for a specific platform.
    - `--force`: Force process for some commands.

=== "Util Commands"
    - `bun util:es5`: Validate ES5 code.
    - `bun util:fix`: Auto-fix syntax errors in the Cocos project.
    - `bun util:check`: Check for syntax errors in the Cocos project.
    - `bun util:unused`: Check for unused code in the Cocos project.
    - `bun util:format`: Format code in the Cocos project.


