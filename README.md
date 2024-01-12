# P-OPT_Repetition
final project of Computer Architecture

代码源于[论文团队](https://github.com/CMUAbstract/POPT-CacheSim-HPCA21)：

如何跑通代码和评估测试：

* 按照[教程](https://tiandiyijian.top/posts/conda%E5%AE%89%E8%A3%85gcc%E5%92%8Cg++/)在conda环境中安装gxx9.3.0和gcc9.3.0；
* 运行 `download_pin.py`下载pin-3.21工具；
* 创建文件夹 `/input-graphs`并将四个图数据 `hugebubbles-00020.sg`、`kron25-d4.sg`、`uk-2002.sg`、`urand25-d4.sg`解压（两个压缩包）到该文件夹，此为仿真的数据输入；
* 运行 `run_cache_sims.py`来开启缓存仿真模拟；
* 运行 `plot_llcmiss_red.py`来绘制每一种缓存替换策略的LLC miss redection指标，此时会输出一个 `llcmiss-red.pdf`文件可视化指标。

其中，可以在 `run_cache_sims.py`和 `plot_llcmiss_red.py`中自定义对比项（数据输入、策略等等）

```python
# run_cache_sims.py
apps        = ['pr']
simulators  = ['lru', 'drrip', 'popt-8b', 'opt-ideal']
versions    = ['baseline','baseline', 'popt', 'opt-ideal']
graphs      = ['uk-2002', 'hugebubbles-00020', 'kron25-d4', 'urand25-d4']
```

```python
# plot_llcmiss_red.py
app         = 'pr'
appNick     = 'PAGERANK'
policies    = ['lru', 'drrip', 'popt-8b', 'opt-ideal']
policyNicks = ['LRU', 'DRRIP', 'P-OPT', 'T-OPT']
versions    = ['baseline', 'baseline', 'popt', 'opt-ideal']
graphs      = ['uk-2002', 'kron25-d4', 'urand25-d4', 'hugebubbles-00020']
graphNicks  = ['UK-02', 'KRON', 'URND', 'HBBL']
```