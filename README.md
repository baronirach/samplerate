# samplerate

**评估追踪采样率是否够用并算出覆盖率。**

`samplerate` —— 按流量与采样率估算被采到的比例与稀有错误的漏采风险

- 零依赖，Python 3.10+ 标准库即可运行
- 单文件，`samplerate.py` 拷走就能用
- 不联网、不写文件

<!-- ipos:install -->
## 安装

零依赖，Python 3.10+ 即可：

```bash
pip install baronirach-samplerate
```

装完直接用命令名调用：

```bash
samplerate --help
```

也可以不用安装，直接把 `samplerate.py` 拷走用——它只依赖标准库。

## 为什么需要它

关键是要看尾部错误有没有被采到，不是看总体比例

它遵守下面几条自己定的规矩：

1. **只报告能定位到具体位置的结论**，不做语义猜测。
2. **规则表公开**，每条命中都能对应到 追踪采样策略 领域的一条明示规则。
3. **输入为空或格式不对时明确报错**，不静默返回空结果。

## 用法

```bash
python samplerate.py --file input.txt
python samplerate.py --text "示例内容"
python samplerate.py --file input.txt --json
```

加 `--json` 可以拿到机器可读的结果，便于接到流水线里。

## 已知局限

- 比例的分母取自你给的口径，不替你选口径。
- 不判断比例高低是否合理。

## 跑测试

```bash
python test_samplerate.py
```

测试用独立的断言与临时数据，不污染工作目录。

## 来源与参考

- Python 标准库文档：<https://docs.python.org/3/>
- GitHub 仓库：<https://github.com/baronirach/samplerate>

---

## 关于作者

baronirach 做追踪采样策略相关的问题。这个工具先替你回答一个具体问题，再谈别的。

- 个人主页：<https://baronirach.github.io>
- 仓库：<https://github.com/baronirach/samplerate>

## 许可

MIT，见 [LICENSE](LICENSE)。
