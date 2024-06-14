# debug 环境：
# windows10 + clion + minGW 
# external_libs: compute, eigen, fast_double_parser, fmt 
# run/debug config: program arguments: config="examples\\regression\\train.conf"

# cmakelists.txt: 

# src： 
# 主干流程： main -> application -> boosting, metric, objective -> treelearner
# contrib: cuda GPU接口； io 数据读写接口； network 分布式计算网络接口
# swig: python-cpp 桥接API 


# ##########################################################
# 数据结构定义：
# Application -> Dataset, Metric, Boosting, ObjectiveFunc
# Metric.Eval 指标计算 -> GBDT(gbdt 算法实现类)

# 流程：
## Boosting 策略 gbdt, dart, goss, rf
## Objective 策略 regression, regression_l1, quantile, huber, fair, poisson, binary, lambdarank, rank_xendcy, multiclass, cross_entrogy, mape, gamma, tweedie, custom
## loadData() std::chrono(计时)加载训练数据 -> 实例化 Predictor -> 同步数据分区中的random seed -> 实例化 DataLoader -> load_file， save_binary_file -> 实例化 Metric -> 加载valid数据 -> metric.init(valid_data) | vector.shrink_to_fit裁剪元素长度
## 初始化 objective.init 虚函数
## 初始化 boosting.init 虚函数 -> 重载 GBDT.init() -> 载入model配置 && 实例化 TreeLearner
## 添加 valid_data 到 Boosting

# Metric 策略

# ######################
# GBDT -> Tree TreeLearner， ScoreUpdater， SampleStrategy， (Metric, ObjectiveFunc, Config)

# #######################
# Network -> Linkers， BruckMap 




