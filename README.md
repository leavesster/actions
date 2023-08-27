# actions

## 基础概念

根据[官方文档](https://docs.github.com/en/actions/learn-github-actions/understanding-github-actions?learn=getting_started&learnProduct=actions)，GitHub Action 主要分以下几个部分：

1. workflow：一个 workflow 代表一次完整的构建流程，包含一个或多个 jobs。
1. events：触发 action 的事件，例如 push、pull request 等。
1. jobs：一个 job 是 workflow 中的一系列 steps 的集合，每一个 step 是一个 actions 或者一个 shell 脚本。jobs 可以并行执行，也可以依赖执行。
1. actions：一个 action 代表 step 中的实际操作内容，可以是一个 shell 脚本、一个 Docker 容器等，属于最小的执行单元。
1. runners：执行 workflow 的服务，可以是 GitHub 托管的服务，也可以是自己搭建的服务。

其中 workflow 是最顶层的概念，一个 workflow 可以包含多个 jobs，一个 job 可以包含多个 steps，一个 step 可以包含多个 actions。

## 复用逻辑

[复用 workflow](https://docs.github.com/en/actions/using-workflows/reusing-workflows) 复用 workflow 最为直接，可以让不同库的 workflow。

同时 workflow 需要在 on 字段上，配置

action 作为一个执行的最小单元，可以通过[自定义 action](https://docs.github.com/en/actions/creating-actions)来给不同的 workflow 进行复用，action 可以作为 composite action，将其他多个 action 合并起来，也可以创建一个完全独立的 action。

## 复用方式

### 复用 workflow：

`{owner}/{repo}/.github/workflows/{filename}@{ref}` for reusable workflows in public and private repositories.
`./.github/workflows/{filename}` for reusable workflows in the same repository.

应该就是 GitHub 地址+ref

### 复用/使用 action

`{owner}/{repo}/{path}@{ref}` path 到 action.yaml 的文件夹。