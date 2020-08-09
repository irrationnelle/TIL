# Typescript 로 mocha 테스트할 때 설정

## `tsconfig.json`

`"module": "commonjs"` 이 부분이 중요.

`esnext` 로 설정하면 `package.json` 에서 `type: module` 로 설정해도 오류 발생.

```json
{
  "compilerOptions": {
    "target": "es5",
    "lib": [
      "dom",
      "dom.iterable",
      "esnext"
    ],
    "allowJs": true,
    "skipLibCheck": true,
    "esModuleInterop": true,
    "allowSyntheticDefaultImports": true,
    "strict": true,
    "forceConsistentCasingInFileNames": true,
    "module": "commonjs",
    "moduleResolution": "node",
    "resolveJsonModule": true,
    "isolatedModules": true,
    "noEmit": true,
  },
  "include": [
    "src"
  ]
}
```

## `package.json`

```json
{
    ...,
    "type": "module",
    ...

}
```

## `.mocharc.json`

```json
{
  "diff": true,
  "extension": ["ts"],
  "package": "./package.json",
  "reporter": "spec",
  "slow": 75,
  "timeout": 10000,
  "ui": "bdd",
  "spec": ["test/*.ts", "test/**/*.ts"],
  "require" : [
    "ts-node/register"
  ]
}
```

