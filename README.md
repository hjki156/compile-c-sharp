# compile-c-sharp
利用 GitHub Action 编译 c sharp

## 功能特性

这个仓库提供了一个手动触发的 GitHub Action 工作流，用于克隆并编译使用了 Windows API 的 C# 项目。

## 使用方法

1. 进入仓库的 **Actions** 标签页
2. 选择 **"编译 C# 项目"** 工作流
3. 点击 **"Run workflow"** 按钮
4. 填写以下参数：
   - **repo_url** (必填): 要克隆和编译的 C# 项目的 Git 仓库 URL
   - **branch** (可选): 分支名称，默认为 `main`
   - **project_path** (可选): 项目文件路径 (.sln 或 .csproj)，如果不指定将自动搜索
   - **build_configuration** (可选): 编译配置，可选 `Release` (默认) 或 `Debug`
5. 点击绿色的 **"Run workflow"** 按钮开始执行

## 工作流程说明

工作流将执行以下步骤：

1. **克隆目标项目**: 从指定的 URL 克隆 C# 项目
2. **设置 .NET SDK**: 自动配置 .NET 6.0, 7.0, 8.0 环境
3. **查找项目文件**: 自动搜索 .sln 或 .csproj 文件（如果未指定）
4. **还原依赖项**: 运行 `dotnet restore` 还原 NuGet 包
5. **编译项目**: 使用指定的配置编译项目
6. **上传产物**: 将编译生成的文件作为 artifacts 上传

## 运行环境

- 运行在 `windows-latest` 环境
- 支持使用 Windows API 的 C# 项目
- 支持 .NET 6.0, 7.0, 8.0 及其框架

## 编译产物

编译完成后，生成的文件将作为 artifacts 自动上传，可以在工作流运行页面下载。
