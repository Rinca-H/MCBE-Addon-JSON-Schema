# JSON Schema
VSCodeで文字を入力すると補完されるやつ。<br>
※ schema = 「スキーマ」

## 使いかた
> [!WARNING]
> VSCode以外で使う想定はしていないので、その場合は自分で何とかしてください。

1. 各JSONスキーマのファイルを好きなところへ置く
2. VSCodeの設定から `settings.json` を開いて `json.schemas` プロパティを追加する
```jsonc
{
  /* ...他の設定項目 */

  "json.schemas": [
    {
      "fileMatch": [
        "**/behavior_packs/*/manifest.json",
        "**/development_behavior_packs/*/manifest.json",
        "**/resource_packs/*/manifest.json",
        "**/development_resource_packs/*/manifest.json"
      ],
      "url": "./json_schemas/manifest.json"
    },
    
    // ...その他のスキーマも同様
  ],

  /* ...他の設定項目 */
}
```
3. `fileMatch` にこのスキーマを適用するファイルを指定し、`url` には1.で置いた場所を指定する<br>**※ アドオンを作る場所は各々で違うと思うので、各自で指定してください**

> [!TIP]
> `fileMatch`の指定について
> - `*` で任意の文字列
>   - `a/*/c.json` なら `a/b/c.json` や `a/xyz/c.json` などにマッチ、`a/x/y/c.json` にはマッチしない
> - `**` で `/` を含む文字列
>   - `a/**/c.json` なら `a/b/c.json` や `a/x/y/z/c.json` などにマッチ

## 設定の例
```json
{
  "json.schemas": [
    {
      "fileMatch": [
        "**/behavior_packs/*/manifest.json",
        "**/development_behavior_packs/*/manifest.json",
        "**/resource_packs/*/manifest.json",
        "**/development_resource_packs/*/manifest.json"
      ],
      "url": "./json_schemas/manifest.json"
    },
    {
      "fileMatch": [
        "**/development_behavior_packs/*/blocks/**/*.json"
      ],
      "url": "./json_schemas/block_dat.json"
    },
    {
      "fileMatch": [
        "**/development_behavior_packs/*/items/**/*.json"
      ],
      "url": "./json_schemas/item_dat.json"
    },
    {
      "fileMatch": [
        "**/development_behavior_packs/*/entities/**/*.json"
      ],
      "url": "./json_schemas/entity_dat.json"
    },
    {
      "fileMatch": [
        "**/development_behavior_packs/*/animation_controllers/**/*.json"
      ],
      "url": "./json_schemas/anicon_dat.json"
    },
    {
      "fileMatch": [
        "**/development_resource_packs/*/entity/**/*.json"
      ],
      "url": "./json_schemas/entity_res.json"
    },
    {
      "fileMatch": [
        "**/development_resource_packs/*/animation_controllers/**/*.json"
      ],
      "url": "./json_schemas/anicon_res.json"
    },
    {
      "fileMatch": [
        "**/development_resource_packs/*/render_controllers/**/*.json"
      ],
      "url": "./json_schemas/rencon.json"
    },
    {
      "fileMatch": [
        "**/development_resource_packs/*/blocks.json"
      ],
      "url": "./json_schemas/blocks.json"
    },
    {
      "fileMatch": [
        "**/development_resource_packs/*/textures/terrain_texture.json"
      ],
      "url": "./json_schemas/terrain_texture.json"
    }
  ]
}
```

## スキーマの対応
|ファイル名|対応するコンテンツ|
|---|---|
|`anicon_dat.json`|アニメーションコントローラ(ビヘイビア)|
|`anicon_res.json`|アニメーションコントローラ(リソース)|
|`block_dat.json`|ブロック(ビヘイビア)|
|`blocks.json`|blocks.json|
|`entity_dat.json`|エンティティ(ビヘイビア)|
|`entity_res.json`|エンティティ(リソース)|
|`item_dat.json`|アイテム(ビヘイビア)|
|`manifest.json`|マニフェスト|
|`rencon.json`|レンダーコントローラ|
|`terrain_texture.json`|terrain_texture.json|

## 参考
- [JSON Schema を自作して、 VSCode で補完させたい - なつねこメモ](https://tech.natsuneko.blog/entry/2022/07/16/create-own-json-schema-with-vscode)
