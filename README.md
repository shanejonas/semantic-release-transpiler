# semantic-release-transpiler
Semantic release plugin to generate typings using the transpiler


## Example:
```
{
  "tagFormat": "${version}",
  "branch": "master",
  "plugins": [
    "@semantic-release/commit-analyzer",
    ["@json-schema-tools/semantic-release-transpiler", {
      "outpath": "./",
      "schemaLocation": "./meta-schema.json",
      "languages": { "ts": true }
    }],
    "@semantic-release/release-notes-generator",
    "@semantic-release/changelog",
    "@semantic-release/github",
    "@semantic-release/git",
    "@semantic-release/npm"
  ],
  "verifyConditions": [
    ["@json-schema-tools/semantic-release-transpiler", {
      "outpath": "./",
      "schemaLocation": "./meta-schema.json",
      "languages": { "ts": true }
    }],
    "@semantic-release/changelog",
    "@semantic-release/npm",
    "@semantic-release/git",
    "@semantic-release/github"
  ],
  "prepare": [
    ["@json-schema-tools/semantic-release-transpiler", {
      "outpath": "./",
      "schemaLocation": "./meta-schema.json",
      "languages": { "ts": true }
    }],
    "@semantic-release/changelog"
  ],
  "publish": [
    ["@semantic-release/github", {
      "assets": [
        "build/generated-typings.js",
        "build/generated-typings.d.ts",
        "build/index.js",
        "build/index.d.ts"
      ]
    }],
    "@semantic-release/npm"
  ],
  "success": [
    "@semantic-release/github"
  ],
  "fail": [
    "@semantic-release/github"
  ]
}
```
