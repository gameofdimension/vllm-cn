# vllm-cn
----
根据 [官方首页文章](https://vllm.ai/)，vllm 能极大提高大语言模型推理阶段的吞吐性能，这对计算资源有限，受限于推理效率的一些情况来说无疑是一大福音
![](https://vllm.ai/assets/figures/perf_a100_n1_light.png)

但是截止 2023.7.8，[vllm 文档](https://vllm.readthedocs.io/en/latest/models/supported_models.html) 显示其尚未支持目前热度较高的一些中文大模型，比如 baichuan-inc/baichuan-7B, THUDM/chatglm-6b

于是本人在另一个 [repo](https://github.com/gameofdimension/vllm) 实现了 vllm 对 baichuan-inc/baichuan-7B 的支持。运行官方的测试脚本，确实也可以看到 5+ 倍的效率提升。目前代码已提交 PR 期望能合并到官方 repo
<pr>
![](img/diff.png)

### 测试

baichuan-inc/baichuan-7B 的 vllm 适配测试可参考 [这里](https://github.com/gameofdimension/vllm-cn/blob/master/vllm_baichuan.ipynb)。也可直接 colab 运行<a href="https://colab.research.google.com/github/gameofdimension/vllm-cn/blob/master/vllm_baichuan.ipynb"><img alt="Build" src="https://colab.research.google.com/assets/colab-badge.svg"></a>。但是因为模型较大，需要选用 A100 gpu 或者更高配置


### 现况
- [chatglm2/3，包括对 tp 的支持](https://github.com/vllm-project/vllm/pull/1558)，code reviewing
- 官方已实现[若干中文大语言模型](https://github.com/vllm-project/vllm/tree/main/vllm/model_executor/models)：aquila，baichuan，qwen

### 感谢

- [NLP（十七）：从 FlashAttention 到 PagedAttention, 如何进一步优化 Attention 性能](https://zhuanlan.zhihu.com/p/638468472)
- [Adding a New Model](https://vllm.readthedocs.io/en/latest/models/adding_model.html)
