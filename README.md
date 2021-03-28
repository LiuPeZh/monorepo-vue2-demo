## monorepo demo
1. yarn install
2. cd packages/mainapp
3. npm run serve
4. 运行错误:
```javascript

> @monorepo-demo/mainapp@0.1.0 serve D:\repository\monorepo-demo\packages\mainap
p
> npx vue-cli-service serve

 INFO  Starting development server...
12% building 18/19 modules 1 active ...norepo-demo\packages\mainapp\src\main.jsD
:\repository\monorepo-demo\packages\mainapp\node_modules\webpack-dev-server\node
_modules\webpack\lib\Dependency.js:237
                throw new Error(
                ^

Error: module property was removed from Dependency (use compilation.moduleGraph.
updateModule(dependency, module) instead)
    at ProvidedDependency.set (D:\repository\monorepo-demo\packages\mainapp\node
_modules\webpack-dev-server\node_modules\webpack\lib\Dependency.js:237:9)
    at iterationDependencies (D:\repository\monorepo-demo\packages\mainapp\node_
modules\webpack\lib\Compilation.js:940:21)
    at D:\repository\monorepo-demo\packages\mainapp\node_modules\webpack\lib\Com
pilation.js:950:8
    at D:\repository\monorepo-demo\packages\mainapp\node_modules\webpack\lib\Nor
malModuleFactory.js:409:6
    at D:\repository\monorepo-demo\packages\mainapp\node_modules\webpack\lib\Nor
malModuleFactory.js:155:13
    at eval (eval at create (D:\repository\monorepo-demo\packages\mainapp\node_m
odules\tapable\lib\HookCodeFactory.js:33:10), <anonymous>:14:1)
    at D:\repository\monorepo-demo\packages\mainapp\node_modules\case-sensitive-
paths-webpack-plugin\index.js:178:9
    at D:\repository\monorepo-demo\packages\mainapp\node_modules\case-sensitive-
paths-webpack-plugin\index.js:125:7
    at D:\repository\monorepo-demo\packages\mainapp\node_modules\case-sensitive-
paths-webpack-plugin\index.js:125:7
    at CaseSensitivePathsPlugin.fileExistsWithCase (D:\repository\monorepo-demo\
packages\mainapp\node_modules\case-sensitive-paths-webpack-plugin\index.js:95:5)
    at D:\repository\monorepo-demo\packages\mainapp\node_modules\case-sensitive-
paths-webpack-plugin\index.js:118:10
    at CaseSensitivePathsPlugin.getFilenamesInDir (D:\repository\monorepo-demo\p
ackages\mainapp\node_modules\case-sensitive-paths-webpack-plugin\index.js:52:5)
    at CaseSensitivePathsPlugin.fileExistsWithCase (D:\repository\monorepo-demo\
packages\mainapp\node_modules\case-sensitive-paths-webpack-plugin\index.js:101:8
)
    at D:\repository\monorepo-demo\packages\mainapp\node_modules\case-sensitive-
paths-webpack-plugin\index.js:118:10
    at Array.<anonymous> (D:\repository\monorepo-demo\packages\mainapp\node_modu
les\case-sensitive-paths-webpack-plugin\index.js:72:5)
    at Storage.finished (D:\repository\monorepo-demo\packages\mainapp\node_modul
es\enhanced-resolve\lib\CachedInputFileSystem.js:55:16)
npm ERR! code ELIFECYCLE
npm ERR! errno 1
npm ERR! @monorepo-demo/mainapp@0.1.0 serve: `npx vue-cli-service serve`
npm ERR! Exit status 1
npm ERR!
npm ERR! Failed at the @monorepo-demo/mainapp@0.1.0 serve script.
npm ERR! This is probably not a problem with npm. There is likely additional log
ging output above.

npm ERR! A complete log of this run can be found in:
npm ERR!  

```
## 目前存在的问题：
  
  因为common子项目中使用了webpack5，导致mainapp运行错误。如果将common子项目中的webpack5依赖删除，然后重新下载依赖，那么mainapp可以正常运行。

  尝试使用 yarn workspace 中的 nohoist 阻止各子项目中node_modules的提升，但运行mainapp还是会报错。

如何解决该问题。
