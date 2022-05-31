# Install Ruby-Prettier on vscode

[[Ruby]]

## How to install prettier on vscode

Launch VS Code Quick Open `Ctrl+P` and paste the following command

`ext install esbenp.prettier-vscode`

## How to install ruby-prettier

1. Open a terminal
2. Enter `ls -la`
3. Enter `cd .vscode/extensions/esbenp.prettier-vscode-<version>`
4. Enter `npm install --save-dev prettier @prettier/plugin-ruby`
5. Wait, then restart VScode

## Setup VScode

1. Launch VS Code Quick Open `Ctrl+Shift+P`
2. Type json and select "Preferences: Open Settings (JSON)
3. Add the folowing code

```json
"[javascript]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
},
"[ruby]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode",
    "editor.formatOnSave": true
},
```

It's done!! 😁
