# assets-builder
Asset files (eg, text, image) bundle tool for Deno.

# Install 

```sh
deno install --allow-read https://raw.githubusercontent.com/Octo8080/assets-builder/main/asset_builder.ts

# Import config file from default ./assets_config.json.
asset_builder >> assets.ts

# Set Import config file.
asset_builder --inport-file my_assets_config.json >> assets.ts
```

# Usage 

```sh
# Import config file from default ./assets_config.json.
deno run --allow-read https://raw.githubusercontent.com/Octo8080/assets-builder/main/asset_builder.ts >> assets.ts

# Set Import config file.
deno run --allow-read https://raw.githubusercontent.com/Octo8080/assets-builder/main/asset_builder.ts --inport-file my_assets_config.json  >> assets.ts
```

# Configuration

The configuration file is described in json.
Do the following:

```json
{
  "files":[
    {
      "importPath": "./sample.txt",
      "calledName": "sample-text"
    }
  ]  
}
```

# Example of using bundled files

```ts example/example.ts
import assets from './assets.ts'

for (const [key, value] of Object.entries(assets.files)) {
  console.log(`key: ${key}, extension: ${value.extension}, content: ${new TextDecoder().decode(value.content) }`);
}
// key: test-text, extension: txt, content: Hello World!!
// key: test-text2, extension: txt, content: Hello World!!
```

