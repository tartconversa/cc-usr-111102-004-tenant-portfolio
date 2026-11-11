# 多业态招商组合的稳健决策分析

本项目保存百货多业态经营研究的合成资料及输入读取工具。当前程序只解析文件并显示输入类型与记录数量，不进行统计分析、模型训练、优化求解或业务推荐。所有记录均为虚构，不能用于陈述真实商场经营结果。

## 输入约定

候选包含不可拆面积、排烟占用、改造费、业态及允许楼层；scenario 净贡献与pair_losses 都以整数元表示。constraints 给出硬容量和覆盖，概率为分子分母。

fixtures 为资料目录，src/portfolio_reader.py 为读取器，tests 为格式读取测试。输入在运行中保持不变；研究计算结果可写入独立的 .workspace-output 目录。

## 本地操作

Python 3.11 及以上版本，现有读取工具只依赖标准库，不需要下载第三方包。进入项目根目录：

    python -m src.portfolio_reader fixtures/candidates.json

编译检查：

    python -m compileall -q src tests

格式读取测试：

    python -m unittest discover -s tests -v

## 固定运行环境

    docker build -t tenant-portfolio:local .
    docker run --rm tenant-portfolio:local

容器默认运行输入测试。镜像使用完整内容摘要固定，研究输入随项目一起复制。
