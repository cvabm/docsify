## github actions
- https://github.com/easimon/maximize-build-space 使编译空间最大化

打印当前文件夹下所有文件夹和文件名（包括子文件夹）

```
        echo "Current Path: $PWD"
        echo "Directories:"
        find . -type d -print
        find . -type d
        echo "Files:"
        find . -type f -print
```

### 编译 apk 并发布 Release

```
name: Build and Release

on:
  push:
    branches:
      - master
      - "feature/*"
    tags:
      - "v*.*.*"
  pull_request:
    branches:
      - master
      - "feature/*"

jobs:
  apk:
    name: Generate APK
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v1
      - name: set up JDK 1.8
        uses: actions/setup-java@v1
        with:
          java-version: 1.8
      - name: set up JDK 1.8
        uses: gradle/gradle-build-action@v2
        with:
          gradle-version: 6.1.1
      - name: Build with Gradle
        run: gradle assembleRelease
      - name: Upload APK
        uses: actions/upload-artifact@v1
        with:
          name: apk
          path: app/build/outputs/apk/release/app-release-unsigned.apk

  release:
    name: Release APK
    needs: apk
    runs-on: ubuntu-latest
    steps:
      - name: Get branch name
        id: branch-name
        uses: tj-actions/branch-names@v5.1
      - name: Print branch
        run: |
          echo "Running on default: ${{ steps.branch-name.outputs.current_branch }}"

      - name: Download APK from build
        uses: actions/download-artifact@v1
        with:
          name: apk
      - name: Create Release
        id: create_release
        uses: actions/create-release@v1
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
        with:
          tag_name: ${{ github.run_number }}
          release_name: ${{ github.event.repository.name }}  ${{ steps.branch-name.outputs.current_branch }} v${{ github.run_number }}.${{ github.run_attempt }}
      - name: Upload Release APK
        id: upload_release_asset
        uses: actions/upload-release-asset@v1.0.1
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
        with:
          upload_url: ${{ steps.create_release.outputs.upload_url }}
          asset_path: apk/app-release-unsigned.apk
          asset_name: ${{ github.event.repository.name }}  ${{ steps.branch-name.outputs.current_branch }} v${{ github.run_number }}.${{ github.run_attempt }}.apk
          asset_content_type: application/zip

```

### react native 编译 apk

```
jobs:
  apk:
    name: Build mobile bundle (Android)
    runs-on: ubuntu-latest
    steps:
     - uses: actions/checkout@v3
     - uses: actions/setup-node@v3
       with:
         node-version: 16
         cache: 'npm'
     - run: npm install
     - name: Build app
       working-directory: android
       run: ./gradlew assembleRelease -PreactNativeArchitectures=arm64-v8a
#      - run: npx react-native run-android
       continue-on-error: true
     - name: Upload APK
       uses: actions/upload-artifact@v1
       with:
         name: apk
         path: android/app/build/outputs/apk/release/app-release.apk
```

### 语法

```
- run: npm install -g bats

actions/upload-artifact
该操作可以将文件或目录上传为工作流运行的一部分，并指定一个名称用于标识这些上传的产物。
这样，在后续的工作流步骤中，您可以使用 actions/download-artifact 操作来下载这些产物。

runs-on: ubuntu-18.04

continue-on-error: true
忽略报错继续执行下一步

```

**actions/checkout@v1 和 actions/checkout@v3 区别**

1、 v3 支持完整的深层克隆（deep clone），可以获取完整的 Git 历史记录，而 v1 只会获取最近的单个 commit。

2、v1 默认情况下检出代码的是默认分支（通常是 master），而 v3 默认情况下会根据触发工作流的事件自动检出相应的分支或拉取请求。

[https://wangchujiang.com/github-actions/](https://wangchujiang.com/github-actions/)
